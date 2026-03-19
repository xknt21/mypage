---
title: "Develop a Web-Based Recipe Manager Application 🧑🏻‍💻"
summary: "Background & Summary"
description: "Background & Summary"
date: 2026-01-09T10:00:01+09:00
author: "Kanato Nishiura"
showToc: true
TocOpen: false
draft: false
hidemeta: false
comments: false
hideSummary: false
ShowReadingTime: true
ShowPostNavLinks: true
---
**Full Documentation**: [Click Here](/pbl4.pdf)

### **1. Project Overview and Strategic Motivation**

The primary purpose of the system is to address the "daily challenge of deciding what to cook" while eliminating the need for scattered notes and screenshots.

* **System Description**: Foood is a web-based platform that integrates recipe storage, weekly meal planning, and automatic shopping list generation.
* **Centralization**: It provides a structured, user-specific experience through secure authentication to reduce the mental burden of managing multiple cooking resources.
* **Persistent Challenges**: The project specifically targets Recipe Disorganization, Time-Consuming Meal Planning, Inefficient Shopping, and Food Waste.
* **Unified Workflow**: By linking recipe management directly with ingredient aggregation, the system streamlines the transition from thinking up a meal to executing a grocery run.

---

### **2. System Objectives and Scope**

The development team identified five core objectives to ensure the platform's utility for home cooks, families, and students.

* **Centralized Recipe Storage**: Implementing a structured database capable of storing ingredients, multi-step instructions, high-quality images, and categorization tags.
* **Intelligent Meal Planning**: Enabling a 7-day planning window with smart randomization features that respect dietary categories.
* **Automated Shopping List Generation**: Aggregating every ingredient from a planned week into a categorized, actionable list.
* **Multi-Device Accessibility**: Utilizing network hosting to allow users to access their plans and lists from any device on their local network.
* **Recipe Sharing**: Implementing a URL-based sharing system for easy distribution and importing of culinary data.

---

### **3. Detailed Functional Requirements (FR)**

The system’s functionality is categorized into five critical modules that define the user experience.

#### **3.1 User and Profile Management**
* **Authentication**: The system supports secure user registration and login utilizing JWT-based session persistence.
* **Configuration**: Users can toggle between "Smart Match" or "Random" modes for the automated planner.

#### **3.2 Recipe Management System**
* **CRUD Operations**: Users have the ability to Create, Read, Update, and Delete recipes.
* **Data Fields**: Each entry supports a title, line-separated ingredients, instructions, tags, and optional image uploads.
* **Discovery**: The interface supports keyword searching, tag-based filtering, and paginated sorting for large collections.

#### **3.3 Weekly Meal Planning**
* **Planning Grid**: A comprehensive $7\times4$ grid representing seven days and four meal slots (Breakfast, Lunch, Dinner, Snacks).
* **Auto-Fill Algorithms**: Support for "Smart Match" which filters recipes by the appropriate meal type tag before assigning them to a slot.

#### **3.4 Shopping List Management**
* **Aggregation**: The system fetches all recipes in the current plan and extracts their ingredients into a single view.
* **Item Management**: Support for checking/unchecking items, bulk actions, and clearing completed items to refresh the view.

#### **3.5 Recipe Sharing Capabilities**
* **Encoding**: Recipes are shared via base64-encoded URLs.
* **Importing**: Recipients can view shared recipes and import them directly into their own accounts with a single confirmation.

---

### **4. Non-Functional Requirements (NFR)**

To ensure professional-grade reliability, the system adheres to several technical standards.

* **Performance**: The system must meet specific targets for API response times and frontend rendering speeds.
* **Usability**: The UI is designed to be mobile-responsive with touch-optimized controls and clear validation feedback.
* **Security**: High priority is placed on secure password storage, token expiration handling, and access control.
* **Maintainability**: The codebase follows RESTful design principles and modular architecture for future scalability.

---

### **5. Architectural and System Design**

The application utilizes a classic **3-tier client-server architecture** to separate the presentation, logic, and data layers.

#### **5.1 Presentation Layer (Frontend)**
* **Technology**: Developed as a Single Page Application (SPA) using **React 19.2** and the **Vite** build tool.
* **Session Management**: JWT tokens are stored in the browser's `localStorage` to maintain a stateless yet secure session.

#### **5.2 Application Layer (Backend)**
* **Framework**: Built with **FastAPI** to ensure high performance and automatic OpenAPI documentation.
* **Subcomponents**:
    * **API Routes**: Manages the endpoint logic for recipes, plans, and users.
    * **Security (JWT Auth)**: Validates every incoming request to ensure only authorized users access data.
    * **Business Logic**: Executes the complex algorithms for meal randomization and ingredient deduplication.

#### **5.3 Data Layer (Database)**
* **Engine**: Uses **SQLite** as a zero-configuration embedded database for ease of deployment.
* **ORM**: Utilizes **SQLAlchemy** to manage relational data through Python classes.
* **Schema**: Consists of nine tables, including core entities like `users` and `recipes`, and junction tables like `recipe_ingredients`.

---

### **6. Behavioral Analysis and Logic**

The project report outlines specific behavioral flows that govern how data moves through the system.

#### **6.1 The Shopping List Workflow**
1.  **Authentication Check**: Validates the user's current session.
2.  **Meal Plan Retrieval**: Fetches the 28-slot grid for the selected week.
3.  **Ingredient Extraction**: Pulls raw ingredient data from every recipe linked to the plan.
4.  **Parallel Operations**:
    * **Aggregation**: Merges duplicate items (e.g., combining 2 eggs from one recipe with 3 eggs from another).
    * **Categorization**: Sorts items into Produce, Dairy, Meat, Grains, Pantry, and Other.
5.  **UI Refresh**: Displays the finalized, sorted list to the user.

#### **6.2 The Recipe Lifecycle**
A recipe moves through various states during its existence:
* **Stored**: The initial state once a recipe is created and saved to the database.
* **In Meal Plan**: A state triggered when a recipe is assigned to a specific day and slot.
* **Being Edited**: A temporary state where the recipe data is being modified by the user.
* **Deletion**: A final action that removes the recipe and all its associated meal plan entries and tags.

---

### **7. Implementation Highlights and Tech Stack**

The development utilized a modern stack to ensure rapid development and reliable performance.

* **Frontend Tools**: React 19.2, Vite, Lucide React for iconography, and standard CSS for styling.
* **Backend Tools**: FastAPI, Pydantic for data validation, and Python-Jose for JWT handling.
* **Security Tools**: Hashing via Passlib to ensure passwords are never stored in plain text.
* **Deployment**: The system is configured to run on a local machine, making it accessible via `localhost` or a network IP for cross-device testing.

---

### **8. Evaluation, Testing, and Validation**

The application underwent a rigorous testing strategy to ensure all functional requirements were met.

* **Multi-Platform Testing**: Validated on Windows, macOS, and Android devices using Chrome and Edge browsers.
* **API Validation**: Endpoints were tested using `curl` commands to verify correct JSON formatting and status codes.
* **Integration Testing**: Monitored terminal logs to verify the seamless flow of data between the React frontend and FastAPI backend.
* **Test Cases**: Sixteen primary test cases were executed, covering everything from user registration (Test 01) to clearing purchased items (Test 16). All sixteen cases achieved a "Pass" status.

---

### **9. Discussion and Future Extensions**

While the system is fully functional, the team identified several challenges and areas for future growth.

* **Key Challenges**: Merging code from different branches led to integration issues, and teammate participation variances increased the workload for active members.
* **UML Utility**: The team credited Use Case and Sequence diagrams for helping identify where authentication checks were strictly required in API calls.
* **Future Roadmap**:
    * **Grocery Realism**: Improving the list logic to normalize measurements into standard retail package sizes.
    * **Nutritional Approximation**: Integrating external APIs to provide calorie and macronutrient data.
    * **Ingredient Substitutions**: Developing a system to suggest alternatives based on dietary needs or ingredient availability.
    * **Cloud Deployment**: Moving the system from a local host to a public cloud environment for universal access.

---

### **10. Conclusion**

The Foood Recipe Manager project successfully delivered a functional full-stack application that addresses the core complexities of home meal management. Despite setbacks encountered during development, the final product demonstrates a coherent solution that integrates authentication, recipe CRUD, and automated planning. The project provided the developers with deep experience in software design, RESTful API architecture, and relational database management. The resulting platform stands as a usable tool that effectively reduces the time and frustration involved in daily cooking and grocery shopping.