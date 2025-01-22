# DOCUMENTATION-HECKATHON-3
DAY 1: LAYING THE FOUNDATION FOR Q-commerce:

Q-Commerce (Quick Commerce): is a fast-paced subset of e-commerce focused on 
rapid delivery. It addresses urgent consumer needs by oAering items within a short 
timeframe, typically under an hour.

Business Goals for Q-Commerce Marketplace:
1.Problem to Solve:
Customers struggle to get essential items like groceries, medicines, and snacks delivered quickly and conveniently.

2.Target Audience:
Busy professionals in urban areas who need rapid delivery of daily essentials.

3.Products/Services Offered:
Groceries: Fresh produce, packaged goods.
Medicines: Over-the-counter and prescription items.
Snacks and urgent essentials: Quick solutions for immediate needs.

4.Unique Selling Points:
Speed: Delivery within 30 minutes, faster than competitors.
Affordability: Competitive pricing with better value for money.
Customization: Personalization options for orders and user preferences.

Data Schema for Q-Commerce Marketplace:
1.Products:
ID: Unique product identifier.
Name: Product name.
Price: Cost per unit.
Stock: Quantity available.
Category: Product classification (e.g., Groceries, Medicine).
Tags: Searchable keywords (e.g., "New Arrival").

2.Orders:
Order ID: Unique order identifier.
Customer Info: Name, contact details, and delivery address.
Product Details: List of products, quantities, and prices.
Status: Order status (e.g., Pending, Shipped, Delivered).
Timestamp: Date and time of order placement.

3.Customers:
Customer ID: Unique customer identifier.
Name: Full name.
Contact Info: Phone and email.
Address: Delivery address.
Order History: Record of past orders.

4.Delivery Zones:
Zone Name: Name or identifier of the zone.
Coverage Area: List of postal codes or cities served.
Assigned Drivers: Details of couriers assigned to the zone.

5.Shipment:
Shipment ID: Unique tracking identifier.
Order ID: Linked order.
Status: Current shipping status (e.g., In Transit, Delivered).
Delivery Date: Expected or actual delivery date.

Relationships Between Entities: 
Customers → Orders.
Orders → Products (via OrderItems).
Orders → Shipments.
Delivery Zones → Customers, Shipments, Assigned Drivers.

DAY 2 PLANNING THE TECHNICAL FOUNDATION:
For technical foundation we need architecture,API,and Data schema.

Q-Commerce Architecture:
1.User Registration:
User signs up → Data is stored in Sanity CMS → Confirmation email or notification is sent to the user.

2.Product Browsing:
User views product categories → Product data is fetched via Sanity API → Products are dynamically displayed on the frontend.

3.Order Placement:
User adds items to the cart → Proceeds to checkout → Order details are saved in Sanity CMS for processing.

4.Shipment Tracking:
Order status updates are fetched from a Third-Party API → Real-time updates are displayed to the user.

 API Requirements:  
o Endpoint Name: /express-delivery-status 
o Method: GET 
o Description: Fetch real-time delivery updates for perishable items. 
o Response Example: { "orderId": 123, "status": "In Transit", "ETA": "15 mins" }

Data Schema Example:
export default { 
name: 'product', 
type: 'document', 
fields: [ 
{ name: 'name', type: 'string', title: 'Product Name' }, 
{ name: 'price', type: 'number', title: 'Price' }, 
{ name: 'stock', type: 'number', title: 'Stock Level' } 
] 
};

DAY 3 - API INTEGRATION AND DATA MIGRATION:

Step 1: 
Create a new Next.js project. 
npx create-next-app. in terminal. 
Install Sanity Studio 
To get started, run this in your command line: 
npm create sanity@latest -- --template clean --create-project "learning-sanityproject" --dataset production

Step 2: 
Open sanity dashboard: 
• NEXT_PUBLIC_SANITY_PROJECT_ID: Found in your Sanity project. 
• SANITY_API_TOKEN: Generate a token by navigating to Settings > 
API > Add API Token in your Sanity dashboard. Give the token 
appropriate read/write permissions - Select Developer. 
• NEXT_PUBLIC_SANITY_DATASET: Set this to production. 

Step 3: 
Configure Environment Variables: 
1.Create a. env. local file in the root of the project directory: 
2.Open. env. local and add the following environment variables: 
o NEXT_PUBLIC_SANITY_PROJECT_ID="{your-sanity-project-id}". 
o NEXT_PUBLIC_SANITY_DATASET="production". 
o SANITY_API_TOKEN="{your-sanity-api-token}". 

Step 4: 
o Make schema in your/sanity/ schemaTypes/food.ts. 
o Import food.ts file in index.ts.

Step 5: 
Make scripts folder in root and in scripts folder form 
importdata.mjs file. (this file has script code that migrate the API 
data in your sanity studio).

Step 6: 
Import Data run the following command: 
npm run import-data 

Step 7: 
Verify the Data in Sanity Studio

Step 8: 
Integrate the date from sanity studio into your next js project 
Through groq Query.

Day 4 - Dynamic Frontend Components – Food tuck Marketplace:

1.Product Listing Page component: 
A grid layout showcasing product data, fetch from sanity 
include  
➢ Product name. 
➢ Product price. 
➢ Product image.  
➢ Product availability.

2.Dynamic Product Detail Page Routing: 
Used Next.js dynamic routes /products/[id]/page.tsx to 
implement individual product pages. 

3.Add to Cart component: 
Customer can add product to the cart, view items, and 
remove items dynamically by the help of 
useshoppingcart library.

4.Checkout component: 
Stripe test account and test API key is used for payment 
gateway.

DAY 5 - TESTING, ERROR HANDLING, AND BACKEND INTEGRATION REFINEMENT:

DAY 5 - TESTING, ERROR HANDLING, AND BACKEND INTEGRATION REFINEMENT:-

Steps for Implementation: 

Step 1: Functional Testing 
Test Core Features:  in which  testing of frontend Product listing,  Filters and search, Cart operations, Dynamic routing .

2. Testing Tools: 

o Postman: For API response testing. 
o React Testing Library: For component behavior testing. 
o Cypress: For end-to-end testing. 

3. How to Perform Functional Testing: 
o Write test cases for each feature. 
o Simulate user actions like clicking, form submissions, and navigation. 
o Validate the output against expected results. 

Step 2: Error Handling  use error message by the use of try catch ,add fallback UI, Test Load Times

Step 4: Cross-Browser and Device Testing in which test on browsing device testing

Step 5: Security Testing   add input validation , secure API COMMUNICATION, TESTING TOOLS 
o OWASP ZAP: For automated vulnerability scanning. 
o Burp Suite: For advanced penetration testing. 

DAY 6 - PREPARATION AND STAGING ENVIRONMENT SETUP DEPLOYMENT 
> Deployment Instructions: 
Step 1: Prepare Your GitHub Repository 
  1. Initialize Your Repository: 
o Create a new GitHub repository or use an existing 
one. 
o Ensure your Next.js project is pushed to the 
repository. 
2. Verify Project Setup: 
o Ensure your Next.js project has a valid package. Json 
file. 
o Check for a. gitignore file with appropriate exclusions 
(e.g., node_modules, env). 
3. Environment Variables: 
o Add a .env file for local development, but do not push 
it to GitHub. Use Vercel's environment variables 
feature for secure storage. 
Step 2: Link GitHub to Vercel 
1. Sign in to Vercel: 
o Go to Vercel and log in with your GitHub account. 
2. Create a New Project: 
o Click on "New Project" in the Vercel dashboard. 
o Select your GitHub repository from the list. 
o If your repository isn't listed, click on "Import Git 
Repository" and provide the URL. 
3. Configure Build Settings: 
o Vercel will auto-detect your project as a Next.js 
application. If not: 
▪ Set Framework Preset to Next.js. 
o Use the default build and output settings: 
▪ Build Command: npm run build  
▪ Output Directory. next. 
Step 3: Add Environment Variables 
1. Define Variables: 
o In the Vercel dashboard, go to the Settings tab of 
your project. 
o Under Environment Variables, add any necessary 
variables (e.g., API_KEY, NEXT_PUBLIC_BASE_URL). 
2. Set Variable Scopes: 
o Add variables for the appropriate environment: 
▪ Production for the live deployment. 
▪ Preview for preview builds. 
▪ Development for local development. 
Step 4: Trigger Deployment 
1. Automatic Deployment: 
o Vercel automatically deploys your application 
whenever you push changes to the connected GitHub 
branch (e.g., main or production). 
2. Preview Deployments: 
o Each pull request will generate a unique preview URL 
for testing. 
3. Manual Deployment (Optional): 
o In the Vercel dashboard, click "Deploy" for manual 
deployments if needed. 
Step 5: Test and Verify Deployment 
1. Check Live Deployment: 
o Vercel provides a domain for your project (e.g., your
project.vercel.app). 
o Visit the URL to verify the deployment. 
2. Custom Domain Setup: 
o Add a custom domain in the Domains section of the 
Vercel dashboard if required. 
3. Monitor Logs: 
o Check the Logs section in the Vercel dashboard for 
any errors during build or runtime.

>  Testing Report (CSV Format):
o Test Case ID
o Test Case Description
o Test Steps
o Expected Result
o Actual Result
o Status
o Severity Level  
o Assigned To 
o Remarks
![Screenshot 2025-01-21 234051](https://github.com/user-attachments/assets/ae0f4336-271d-4c55-8ebe-63b2057422e1)





 
> Performance testing tools (e.g., Lighthouse,GTmetrix) for validate the application performance ,speed and SEO.







![Screenshot 2025-01-22 103906](https://github.com/user-attachments/assets/0cb30a5d-8a84-4480-bd57-ca5c1237d906)

