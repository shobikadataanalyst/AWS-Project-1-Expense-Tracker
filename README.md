# AWS-Project-1-Expense-Tracker
# Personal Expense Tracker

## Project Overview
The **Personal Expense Tracker** is a **serverless web application** that allows users to track their daily expenses. Users can add expense entries including **date, category, amount, and optional notes**. This project demonstrates **end-to-end cloud deployment** and **serverless architecture** using AWS services.

The frontend is deployed on **Vercel** for public access, while the backend is handled by **AWS Lambda** and **API Gateway**, storing data in **DynamoDB**.

---

## Features
- Add daily expenses with relevant details
- Serverless architecture with **AWS Lambda + API Gateway**
- Data stored in **DynamoDB**
- Publicly accessible frontend hosted on **Vercel**
- Responsive design for mobile and desktop

---

## Technology Stack
- **Frontend:** HTML, CSS, JavaScript
- **Backend:** AWS Lambda
- **API Management:** AWS API Gateway
- **Database:** AWS DynamoDB
- **Hosting:** Vercel (frontend), AWS (backend)

---

## Setup Instructions

### Backend
1. Create a **DynamoDB table** named `Expenses`:
   - Partition Key: `userId`
   - Sort Key: `date`
2. Create an **AWS Lambda function** `add_expense` and grant it write permissions to DynamoDB.
3. Set up **API Gateway** POST method `/add-expense` → connect it to the Lambda function.
4. Enable **CORS** in API Gateway to allow frontend requests.

### Frontend
1. Update `index.html` → replace the `fetch` URL with your **API Gateway URL**:

```javascript
const response = await fetch('https://YOUR_API_GATEWAY_URL/add-expense', {
    method: 'POST',
    headers: {'Content-Type':'application/json'},
    body: JSON.stringify(data)
});
