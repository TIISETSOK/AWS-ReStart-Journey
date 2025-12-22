# AWS Group 5 Presentation: Marble Bistro Serverless Modernization

<img width="1348" height="761" alt="image" src="https://github.com/user-attachments/assets/2d19ac47-5c0e-46cb-b0b3-b082935f9c25" />


## Company Overview

* **Marble Bistro** is a successful, bistro-themed local restaurant.
* The business is struggling with manual systems that cannot keep up with growing customer demand.
* They receive multiple bookings and orders from in-person customers, via phone, or via email.
* Their current manual system causes numerous issues.
* The owner requires a cost-effective, simple modernization solution.
* AWS serverless architecture is the perfect fit for this solution.

---

## Challenges

These challenges are costing the restaurant both money and reputation.

### Operational & Infrastructure Issues

* **Lack of Cloud Infrastructure**: Total dependence on manual processes and on-premises systems.
* **Operational Inefficiencies**: Issues such as order mix-ups, incorrect dishes delivered, and frequent errors. Order errors lead to food waste and unhappy customers.
* **Double Bookings**: The absence of a centralized system results in reservation conflicts. Double bookings damage trust.
* **Confirmation Delays**: Manual processes hinder timely customer communication.

### Data Management & Scaling Limitations

* **Inadequate Customer Data Management**: Difficulty in tracking repeat customers or special requests. The inability to track preferences means missed opportunities for personalized service.
* **Scaling Limitations**: Growth necessitates costly staff or hardware upgrades. The current system doesn't scale; handling more customers means proportionally more staff and infrastructure costs.

---

## Solution Architecture

We will build a static website with a **serverless backend**. This architecture leverages AWS serverless services for maximum efficiency and minimal cost.

### AWS Services Used

| Service | Function in Solution |
| :--- | :--- |
| **S3** | Stores static files (website, menu PDFs, photos) and backups cheaply without managing servers. Used for reliable static hosting. |
| **CloudFront** | Delivers the website and images quickly to customers worldwide by caching content at edge locations. Used for speed and HTTPS. |
| **API Gateway** | Creates secure APIs that connect the website to backend systems. Triggers Lambda functions when customers make bookings/orders. |
| **Lambda** | Runs the backend code for order processing and inventory checks without managing servers, paying only for actual usage. Used for pay-per-execution compute. |
| **DynamoDB** | Stores operational data like orders, customer profiles, and menu items in a fast, scalable database. Used for flexible data storage without database management. |
| **SES (Email)** | Sends automated emails for order confirmations, reservation reminders, and promotional offers at low cost. Used for cost-effective email delivery. |

### Architecture Flow

1.  The static website (HTML/CSS/JS) is hosted on S3 and delivered globally via **CloudFront** CDN.
   <img width="1241" height="538" alt="Screenshot 2025-12-15 051137" src="https://github.com/user-attachments/assets/bf7739ff-8edb-4cad-b549-4cd11655dec2" />

3.  When customers make bookings or orders, **API Gateway** triggers **Lambda** functions.
<img width="1236" height="551" alt="Screenshot 2025-12-15 051214" src="https://github.com/user-attachments/assets/446f298b-982b-443d-b44b-256221738195" />

   
5.  The Lambda functions store data in **DynamoDB** and send confirmations via **SES**.
6. 
7.  This setup is highly scalable, pay-per-use, and requires no server management.

---

## Final Website 
<img width="1904" height="940" alt="Homepage-Screenshot" src="https://github.com/user-attachments/assets/e7d00fce-0660-424c-954e-baafbc8eded4" />

**The booking page**
<img width="1902" height="943" alt="Booking-Form" src="https://github.com/user-attachments/assets/6673c934-85d8-47f0-b9e1-f9f8dca41340" />

<img width="1917" height="938" alt="Booking-Confirmation" src="https://github.com/user-attachments/assets/cc6ce34d-ea2d-4975-9ce7-91119c13182f" />


## Benefits and Cost Analysis

### Cost Savings

* **Cost Reduction**: Achieves a 95% cost reduction versus traditional hosting.
* **No Upfront Investment**: No upfront infrastructure investment is needed.
* **Pay-per-Use**: Pay only for actual usage.
* **Estimated Cost**: For a small restaurant, AWS costs approximately **$1–2 per month** using free tier services plus minimal charges for SES ($0.10). Traditional hosting would cost $50–$200/month.

### Operational Benefits

* **Performance**: Delivers fast global loading through CloudFront CDN with 99.99% uptime and automatic scaling during peak dining hours.
* **Operations**: Eliminates booking errors, automatically tracks customer preferences, and sends instant confirmations without manual work. Staff can focus on service instead of paperwork.
* **Scaling**: The system scales automatically—the infrastructure adapts without intervention, whether they serve 10 customers or 1000.
* **Security**: Protects customer data with default HTTPS encryption, CloudFront DDoS protection, and automated backups.

---

## Implementation Timeline

The entire solution can be deployed in under a month, making it practical and achievable.

| Timeline | Phase |
| :--- | :--- |
| **Week 1 – 2** | Website development and AWS infrastructure setup. |
| **Week 3** | Testing and staff training. |
| **Week 4** | Go-live and monitoring. |

---

## Conclusion

This project demonstrates how modern cloud architecture solves real business problems affordably.

* AWS serverless architecture provides enterprise capabilities at minimal cost.
* Static website + Lambda backend eliminates server management overhead.
* Estimated monthly cost: $1–2 (vs $50–$200 traditional hosting).
* It is a scalable solution that grows with business success.
