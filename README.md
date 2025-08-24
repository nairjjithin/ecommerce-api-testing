# ShoppersStack API Testing

ShoppersStack is an e-commerce web application that testers use for practicing software testing.  
This project demonstrates API testing using Postman and Newman, designed to showcase professional QA practices.

---

## Project Overview
The objective of this project is to design, automate, and validate key API workflows of an e-commerce system:
- Authentication and Login
- Product listing
- Wishlist
- Cart operations
- Address management
- Order creation and payment

This project includes mocking, schema validation, data-driven testing, and HTML report generation.

---

## What We Implemented

### API Collection and Tests
- Created a Postman collection covering core e-commerce APIs.
- Wrote test scripts to validate response codes, payloads, and workflows.

### Mocking
- Created a mock payment server in Postman to simulate payment gateway/bank responses.
- Forced order workflows to depend on the mock payment responses, ensuring realistic order flows without relying on a live bank API.

### Schema Validation
- Used JSON schema validation for API responses.
- Schemas are stored locally in `/schemas` and also accessible directly from GitHub.

### Happy Path and Negative Testing
- Designed a complete Happy Path (successful order placement).
- Validated with negative scenarios to confirm proper error handling.

### Data-Driven Testing
- Parameterized test data using a CSV (`collections/data/ShoppersStack_data.csv`).
- Covered multiple scenarios (valid/invalid login, order, payment responses).

### Reporting
- Used Newman CLI to run collections outside Postman.
- Generated HTML Extra reports with detailed request/response logs.
- Reports saved in `/reports` folder (gitignored).

---

## Project Structure
```
├── collections/
│ ├── ShoppersStack API Testing.postman_collection.json
│ ├── ShoppersStack_Staging.postman_environment.json
│ └── data/
│ └── ShoppersStack_data.csv
├── schemas/ # JSON schemas for response validation
├── reports
```

## How to Run Locally

### Prerequisites
- Node.js installed
- Newman installed globally:
  ```bash
  npm install -g newman newman-reporter-htmlextra
Run Tests
From repo root:
newman run collections/"ShoppersStack API Testing.postman_collection.json" \
  -e collections/"ShoppersStack_Staging.postman_environment.json" \
  --iteration-data collections/data/ShoppersStack_data.csv \
  --folder "Scenario: Happy Path — Login-Mock Pay-Order" \
  -r cli,htmlextra \
  --reporter-htmlextra-export reports/run-report.html \
  --insecure
View Reports
Open reports/run-report.html in any browser.

Screenshots
1. Mock Server Setup
<img width="1911" height="1013" alt="image" src="https://github.com/user-attachments/assets/bd1498f7-5b0e-4b62-a15d-1859ada37133" />

<img width="1886" height="952" alt="image" src="https://github.com/user-attachments/assets/05d32d81-659a-4e66-b707-6a0b45ff9812" />

2. Data-Driven Test Results
<img width="1197" height="851" alt="image" src="https://github.com/user-attachments/assets/9c5df809-53f4-4b65-945a-ac8587cc1615" />


3. HTML Report
<img width="1080" height="885" alt="image" src="https://github.com/user-attachments/assets/cc896a53-e94a-4af2-bb78-c026304e44fb" />


## Future Enhancements
Jenkins CI/CD integration to run tests automatically on commit or schedule.

JUnit report generation for Jenkins test trends.

Monitoring and alerting (Slack/email) for test failures.

More advanced mocking and additional negative scenarios.

## Skills Demonstrated
API testing with Postman and Newman

Mock server setup for dependency isolation

Schema validation and contract testing

Data-driven testing with CSV input

Test reporting and documentation

Designing end-to-end test flows (Happy Path and Negative cases)
