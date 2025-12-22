# Architecture Design Document: IAM Security Training Chatbot

<img width="916" height="395" alt="image" src="https://github.com/user-attachments/assets/7f1153ef-b1dc-40bf-aef4-5a4b3076aab0" />




**Prepared by:** Group 6 - AWS re/Start Program  
**Project 3:** Cloud Learners Inc. Interactive IAM Quiz Bot  
**Date:** December 18, 2025

---

## Overview

This document outlines the serverless chatbot we built to teach AWS Identity and Access Management through scenario-based questioning. Our differentiator is creating a space where students make real decisions, mess up safely, and learn before mistakes become production disasters.

**What Are Chatbots?**  
Programs that simulate conversations using natural language processing. We built ours for education using AWS Lex, Amazon's conversational AI service.

---

## Why IAM Over S3? Three reasons:

1. **40% of cloud security breaches stem from IAM misconfigurations**
2. **Every AWS user touches IAM daily** (you can skip S3, but not identity management)
3. **We identified three confusion points students consistently face:**
   - Mixing up IAM Users and Roles
   - Not understanding Authentication vs Authorization
   - Over-permissioning with Administrator Access

These aren't academic problems. We've watched teams make these exact mistakes in real environments.

### **Architecture:**  
Serverless design with Amazon Lex V2 (conversation layer) and AWS Lambda (business logic). Deployed in Cape Town (af-south-1) using English (ZA) as required. Scales automatically with minimal cost.

---

## Service Selection & Rationale

### 1. Amazon Lex V2: The Conversation Layer

Amazon Lex is AWS's chatbot service powered by the same technology behind Alexa. It handles language understanding and conversation flow management.

**Key Configuration:**
- Bot: `CloudLearnersSecurityBot`
- Language: English (ZA) – project specification requirement
- Intents: `IAMInfo` (Part 1) and `IAMQuiz` (Part 2)
- Slot Type: `QuizAnswer` (A/B/C options)
- Utterances: Progressed from 1 (Part 1 requirement) to 7 (Part 2)

We chose V2 for superior multi-turn conversation handling and better Lambda integration.

### 2. AWS Lambda: The Intelligence

Lambda provides the conditional logic Lex cannot handle alone. The project required branching: IF correct then next question, IF incorrect then explain why. This needs executable code.

**Implementation:**
- 3-question quiz with 4 distinct conversation paths
- Input normalization via regex (handles "B", "b", "answer is B")
- Error handling with try-catch blocks
- CloudWatch logging at every decision point

Production-grade code with helper functions, null checks, and extensive comments.

### 3. CloudWatch: Monitoring & Debugging

Serverless functions run ephemerally in AWS infrastructure. CloudWatch logs every intent trigger, slot capture, answer normalization, branching decision, and error. Critical for troubleshooting.

---

## Meeting Project Requirements

### Part 1: Foundation Build

**Requirement:** One intent, one utterance.  
**Delivered:** `IAMInfo` intent with single utterance "What is IAM?"  
Response positions IAM as "the first line of defense in Cloud Security."

This constraint taught intent recognition fundamentals. We documented three test cases showing functionality and limitations before Part 2 expansion.

### Part 2: The Challenge

**Requirements:**
- Quiz with branching logic
- Clear feedback for correct/incorrect answers
- Engaging educational experience
- Stakeholder presentation with live demo

**Delivered:**
- 3-question scenario-based quiz (not definition-based)
- 4 distinct conversation paths based on correctness
- Educational feedback explaining real-world consequences
- Natural language input handling
- Professional presentation (see attached PowerPoint)

**Key Differentiator:**  
We asked "Your EC2 needs S3 access. IAM User or Role?" instead of "What is an IAM Role?" Wrong answers trigger teaching moments with production consequences explained, transforming evaluation into education.

---

## Challenges & Solutions

### 1. Lambda Permission Denied

**Problem:** Built everything, got "Access Denied" errors with no clear explanation.  
**Root Cause:** Lambda requires explicit resource-based policy granting `lex.amazonaws.com` invoke permissions. AWS security is deny-by-default.  
**Learning:** We were teaching IAM security while IAM permissions blocked us. The irony was educational.  
**Solution:** Lambda Console → Configuration → Permissions → Resource-based policy → Grant `lex.amazonaws.com` invoke rights.

### 2. "Intent IAMQuiz is Fulfilled" Bug

**Problem:** Invalid input like "xyz123" caused Lex to mark intent as fulfilled instead of handling gracefully.  
**Root Cause:** Custom slot type configured with "Restrict to slot values" AND synonyms. AWS doesn’t allow this combination. Lex blocked input instead of passing to Lambda for intelligent handling.  
**Learning:** Slot configuration directly impacts user experience. Restrictive settings create rigid interactions.  
**Solution:** Changed to "Expand values" and removed synonyms. Lambda's `normalizeAnswer()` now validates input and provides helpful error messages.

### 3. Natural Language Input Handling

**Problem:** Expected "B", users typed "I think the answer is B" or lowercase "b".  
**Root Cause:** Initial code checked exact matches. Real users are conversational, not programmatic.  
**Solution:** Implemented regex pattern `/[ABC]/` to extract first valid letter from any input format. Handles variations seamlessly while maintaining validation.

### 4. Response Formatting

**Problem:** Bot responses ran together with no visual separation between questions and options.  
**Root Cause:** Standard line breaks insufficient for chat interface constraints.  
**Solution:** Added visual separators, strategic line breaks, clear section headers (QUESTION 1 OF 3), and proper spacing. Formatting as information architecture for scannable content.

---

## Design Trade-offs

### Serverless vs Traditional Architecture
- **Choice:** Serverless for zero infrastructure management and pay-per-use pricing
- **Trade-off:** Harder debugging, mitigated with comprehensive CloudWatch logging

### Three Questions vs More
- **Rationale:** Each question addresses one specific IAM confusion point
- **Testing:** 2–3-minute completion time, substantive without being tedious
- **Scalability:** Architecture supports 20+ questions when needed

### IAM vs S3 Topic
- **Strategic Decision:** S3 was safe; IAM was strategic
- **Justification:** 40% of breaches involve IAM. Storage is a feature; security is a foundation
- **Result:** Immediately applicable to production safety, not just certification prep

---

## Key Takeaways

### 1. Constraints Accelerate Learning
Part 1's "one utterance" rule forced us to master fundamentals before adding complexity. Limitations become teachers when approached correctly.

### 2. Branching Logic is the Differentiator
Anyone can build a bot that answers "What is IAM?" Value emerged from conditional logic: IF wrong THEN explain consequences AND offer retry. This transforms information retrieval into education.

### 3. Context Creates Memory
Scenario-based questions ("Your EC2 needs S3 access - what do you use?") outperform definition recall ("What does IAM stand for?"). Context mirrors real-world application.

### 4. Production Code Matters
Input normalization, error handling, and logging separate demos that work during testing from tools that survive real users doing unpredictable things.

---

## Conclusion

The project asked for a quiz bot. We delivered an educational tool backed by research (40% breach statistic, identified confusion points), implemented with production-quality code (error handling, input normalization, comprehensive logging), and presented professionally with business justification.

Our architecture addresses real IAM confusion through scenario-based questions, handles messy user input gracefully through Lambda validation, scales automatically via serverless design, and costs under $3 for 1,000 quiz completions.

This isn't just meeting requirements. It's understanding why requirements exist and building something that matters beyond the assignment. We chose IAM because security is foundational, not optional. We implemented branching logic because education requires teaching moments, not just answer validation. We documented challenges because real learning comes from solving problems, not following tutorials.

**Final Insight:**  
We set out to build a chatbot for Cloud Learners Inc. We ended up learning more about AWS IAM, Lambda, Lex, and production system design than any tutorial could teach. That's project-based learning with real constraints, real problems, and real consequences for design decisions.
