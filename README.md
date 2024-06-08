# URL Shortener with QR Code Generation and Telemetry Tracking

## Project Overview
This project aims to develop a comprehensive URL shortening service similar to Bitly, with additional functionalities such as QR code generation and detailed usage tracking. The service will be built using the MERN stack (MongoDB, Express, React, Node.js) and hosted on Microsoft Azure, utilizing Azure Functions, Azure Blob Storage, and Azure Cosmos DB. This project will provide users with the ability to create short URLs, generate corresponding QR codes, and track usage statistics through intuitive graphs and analytics.


![Screenshot 2024-06-08 153802](https://github.com/PrinceSinghhub/urlShortener/assets/71000042/dca6a8e0-b1fd-4bee-80d5-f7049dee06cf)

## Source Code Not Uploaded Due to the Copy & Pasting ⚠️
## Objectives

### URL Shortening:
- Convert long URLs into short, manageable links.
- Ensure the shortened URLs are unique and map back to the original URLs.

### QR Code Generation:
- Automatically generate QR codes for each shortened URL.
- Store and manage QR code images efficiently.

### Telemetry Tracking:
- Track the number of clicks on each shortened URL.
- Provide detailed statistics and graphs to visualize link usage.

### Azure Integration:
- Host the application on Azure Web App for scalability and reliability.
- Use Azure Functions for handling asynchronous tasks like QR code generation.
- Store URL and QR code data in Azure Cosmos DB and Azure Blob Storage.

## Technical Approach

### Planning and Design

**Requirement Analysis:**
- Identify and document all functional and non-functional requirements.
- Define the project scope and create a detailed project plan.

**Database Design:**
- Design a schema for MongoDB to store URL mappings, click counts, and QR code data.
- Ensure the schema supports efficient querying and data retrieval.

**Flowchart and Architecture:**
- Develop a flowchart to visualize the overall process and data flow.
- Design the system architecture, including frontend, backend, and Azure services integration.

### Development

**Frontend Development:**
- Create a user-friendly interface using React.
- Implement forms for URL input and display sections for shortened URLs, QR codes, and analytics.

**Backend Development:**
- Set up an Express server to handle API requests.
- Implement endpoints for creating short URLs, redirecting to original URLs, generating QR codes, and tracking clicks.
- Use Node.js for server-side logic and data processing.

**URL Shortening Approach:**
- Implement a Base64 encoding algorithm to create unique short URLs.
- Store the original URL and its encoded counterpart in MongoDB.
- Ensure efficient mapping and retrieval of URLs for redirection.

**QR Code Generation:**
- Use a library like qrcode to generate QR codes for each shortened URL.
- Store QR codes in Azure Blob Storage.
- Save the URL of the QR code image in the MongoDB database for quick access.

**Telemetry Tracking:**
- Implement a mechanism to count clicks on each shortened URL.
- Store click data (timestamps, user info) in MongoDB for detailed analytics.
- Provide API endpoints to fetch analytics data for the frontend.

### Deployment

**Database Connection:**
- Connect the application to Azure Cosmos DB using MongoDB API.
- Ensure secure and optimized database access and query execution.

**Azure Web App Deployment:**
- Deploy the React frontend and Express backend to an Azure Web App.
- Configure continuous integration and deployment pipelines using Azure DevOps.

**Azure Functions:**
- Use Azure Functions to offload intensive tasks such as QR code generation.
- Integrate Azure Functions with the main application for seamless operation.

**Azure Blob Storage:**
- Configure Azure Blob Storage to securely store QR code images.
- Set appropriate access controls and permissions for blob storage.

![AzUrlShortener (1)](https://github.com/PrinceSinghhub/urlShortener/assets/71000042/39b6b50e-d35a-45ae-ba52-fbcac0809c0b)

### Testing and Optimization

**Unit Testing:**
- Write and execute unit tests for individual components of the application.
- Ensure all functions and methods perform as expected.

**Integration Testing:**
- Test the integration between different components (frontend, backend, database, Azure services).
- Identify and resolve any issues in the data flow and communication.

**Performance Optimization:**
- Optimize database queries for faster data retrieval.
- Improve the efficiency of the URL encoding/decoding process.
- Enhance the performance of QR code generation and storage.

## Components

### User Interface (UI)
- **Input for URL:** A text box for users to input the URL they want to shorten.
- **Display Short URL:** A section where the generated short URL is displayed.
- **Display URL Statistics:** A dashboard to show various statistics like the number of clicks, timestamp of creation, etc.
- **QR Code Generator:** A feature to generate and display a QR code for any given short URL.
- **URL Management:** An interface to list, edit, or delete URLs.
- **Graphical Representation:** Charts and graphs to visualize URL usage data.

### Backend System
- **URL Encoder (Base64):** A module that converts the original URL into a Base64 encoded string.
- **Database Interface:** A system to handle storing, retrieving, updating, and deleting URL data.
- **API:** Set of endpoints to handle interactions between the UI and the database, including CRUD operations and data retrieval for statistics.

### Database
- **Table Structure:** Stores essential data like the original URL, short URL, creation timestamp, and click count.
- **Data Management:** Ensures efficient storage and retrieval of URL data, handles incrementing click counts, and provides data for statistical analysis.

## Video 📽️


## Step-by-Step Process

### User Input and URL Shortening
1. **User enters the URL in the UI.**
2. **The system encodes the URL using Base64 encoding.**
3. **A unique short URL is generated by linking the Base64 encoded part with the original URL.**
4. **Store the original URL, short URL, timestamp, and initial click count (0) in the database.**

### Storing URL Data
1. **Receive the short URL, original URL, timestamp, and click count.**
2. **Insert this data into the database.**
3. **Confirm storage and return the short URL to the user.**

### Managing URLs
1. **User can view all stored URLs on the UI.**
2. **System fetches data from the database to display original URLs, short URLs, timestamps, and click counts.**
3. **User can perform CRUD operations (Create, Update, Read, Delete) on their URLs.**

### Generating QR Codes
1. **User selects a short URL to generate a QR code.**
2. **The system generates the QR code corresponding to the short URL.**
3. **Display the QR code on the UI for the user to download or share.**

### Tracking URL Clicks
1. **When the short URL is accessed, the system increments the click count in the database.**
2. **Record the timestamp of each click (optional).**
3. **Provide updated statistics to the user.**

### Displaying Statistics and Graphs
1. **Fetch URL data from the database.**
2. **Generate graphical representations of data (e.g., click counts over time).**
3. **Display these graphs on the user interface.**

### Schema Design
**URLs Table:**
- id: Unique identifier
- original_url: Original URL provided by the user
- short_url: Generated short URL
- timestamp: Time when the URL was created
- click_count: Number of times the short URL was accessed

## Diagram

```
graph TD
    A[User Interface] -->|Enter URL| B[URL Encoder (Base64)]
    B --> C[Generate Short URL]
    C --> D[Database]
    D -->|Store Data| E[Short URL]
    E --> A

    subgraph Database
    D1[URLs Table]
    end

    A -->|View URLs| F[Fetch URL Data]
    F --> D
    D --> F1[Display URL Data]

    A -->|Generate QR Code| G[QR Code Generator]
    G --> H[Display QR Code]

    A -->|Track Clicks| I[Increment Click Count]
    I --> D

    A -->|View Statistics| J[Fetch Statistics]
    J --> D
    D --> J1[Generate Graphs]
    J1 --> A

    A -->|CRUD Operations| K[Perform CRUD]
    K --> D
    D --> K1[Update Database]
```

## Expected Outcomes

- A fully functional URL shortening service providing short URLs and QR codes.
- Real-time tracking and analytics of URL usage, displayed through interactive graphs.
- A scalable and reliable application hosted on Azure, leveraging cloud services for optimal performance.
- Enhanced problem-solving and development skills through the implementation of encoding algorithms and cloud integration.

## Important Outcomes

- Developing a hashing algorithm requires strong problem-solving skills and a good understanding of data structures and algorithms.
- Maintaining the state dynamically to update the database in real-time when a link is clicked.
- Generating barcodes dynamically based on user input and learning new barcode generation logic.

## Conclusion

This project involves the development of a sophisticated URL shortening service with additional features such as QR code generation and telemetry tracking. By utilizing the MERN stack and integrating with Azure services, the project aims to deliver a comprehensive solution that meets user needs while offering a seamless and efficient user experience. The project will not only serve as a practical application of modern web technologies but also provide valuable insights and learning opportunities in cloud computing and full-stack development.

---

## How to Start

We will start by hosting the system locally using the MERN stack. After creating the full backend and frontend, we will replace all the local services with Azure services for centralized use and hosting, including the database.

### Steps:

#### Local Development with MERN Stack
1. **Begin by setting up a local development environment using the MERN stack (MongoDB, Express, React, Node.js).**
2. **Develop the full backend and frontend functionalities locally.**
3. **Test the complete system to ensure all

 features are working correctly.**

#### Transition to Azure Services
1. **Once the local development is complete and tested, start the migration to Azure services.**
2. **Replace the local backend services with Azure equivalents (e.g., Azure App Services for hosting Node.js applications).**
3. **Migrate the MongoDB database to Azure Cosmos DB for a centralized and scalable database solution.**
4. **Host the frontend on Azure Static Web Apps or Azure App Services.**

#### Centralized Hosting and Database Management
1. **Configure Azure services to work seamlessly together, ensuring the system is fully functional in a cloud environment.**
2. **Set up continuous integration and continuous deployment (CI/CD) pipelines to automate the deployment process.**
3. **Monitor and manage the application using Azure's monitoring tools and services to ensure reliability and performance.**

By following these steps, we can start with a local development environment using the MERN stack and then transition to Azure services for centralized hosting and database management.
