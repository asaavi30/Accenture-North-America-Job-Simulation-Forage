# Task One: Object Oriented Programming

## Write a class to perform search on an interactive website.

### Solution: SearchController Implementation
The SearchController is a Spring Boot REST controller that handles product search functionality. It allows users to search for products by querying the product name or description. The search can be either an exact match (when the query is wrapped in quotes) or a case-insensitive partial match.

#### Key Features:
* Endpoint: /api/products/search
* Query Parameter: query (the search term)
* Exact Match: If the query is wrapped in quotes ("query"), it performs an exact match on the product name or description.
* Case-Insensitive Search: If the query is not wrapped in quotes, it performs a case-insensitive search.
* Filtering: The search logic filters products based on whether the query matches the product name or description.

#### Code Structure:
* Controller: SearchController.java
* Repository: ProductItemRepository (used to fetch all products)
* Model: ProductItem (represents a product with name and description fields)

#### Example Usage:
* Exact Match: /api/products/search?query="Cool Shirt"
* Partial Match: /api/products/search?query=cool

# Task Two: Code Refactoring

## Consolidate copy/pasted code into a central location.

### Solution: Refactoring and Reporting
In Task 2, the search functionality was refactored into a SearchService to improve code modularity and reusability. Additionally, a ReportController was introduced to generate a daily report of product counts for specific important terms (e.g., "Cool", "Amazing", "Perfect", "Kids").

#### Key Features:
* SearchService: The search logic was moved from SearchController to SearchService to separate concerns and make the code more maintainable.
* ReportController: Generates a report of product counts for predefined important terms.
  * Endpoint: /api/products/report
  * Response: Includes total product count and the number of products matching each important term.

#### Code Structure:
* Controller: SearchController.java (now delegates search logic to SearchService)
* Service: SearchService.java (handles the search logic)
* ReportController: ReportController.java (generates product count reports)
* Response Model: SearchReportResponse (contains the report data)

#### Example Usage:
* Report Endpoint: /api/products/report
* Response Example:
  * {
  "productCount": 100,
  "searchTermHits": {
    "Cool": 10,
    "Amazing": 5,
    "Perfect": 3,
    "Kids": 15
  }
}

# Task Three: Continuous Integration

## Set up automated builds to validate code changes on every push.

### Solution: Jenkins Pipeline Configuration
Task 3 involves setting up a Jenkins pipeline to automate the build and test processes for the project. The pipeline is defined using Jenkins' declarative pipeline syntax and consists of two main stages: Build and Test.

#### Key Features:
* Pipeline Structure: The pipeline is divided into stages, each representing a phase of the CI/CD process.
* Build Stage: Compiles the project using Gradle.
* Test Stage: Runs the project's test suite using Gradle.

#### Pipeline Configuration:
* Agent: The pipeline can run on any available agent (agent any).
* Stages:
  * Build: Executes the ./gradlew assemble command to compile the project.
  * Test: Executes the ./gradlew test command to run the project's tests.

#### Code Example: (https://www.jenkins.io/doc/book/pipeline/syntax/#stages)
* pipeline {
    agent any
    stages {
        stage("Build") {
            steps {
                sh "./gradlew assemble"
            }
        }
        stage("Test") {
            steps {
                sh "./gradlew test"
            }
        }
    }

#### Example Usage:
* When a developer pushes code to the repository, the Jenkins pipeline is triggered automatically.
* The pipeline runs the Build and Test stages, and the results are displayed in the Jenkins dashboard.
* If any stage fails, the pipeline stops, and the team is notified to investigate and resolve the issue.

# Task Four: Agile Planning

## Write stories for a new feature to help plan the next sprint.

### Solution: Task 4 outlines user stories and acceptance criteria for an e-commerce platform. These stories cover various functionalities related to shopping cart management, checkout process, and order notifications.

#### Key Stories:

* Shopping Cart Management:
  * Add items to the cart.
  * View items in the cart.
  * Remove items from the cart.
  * Change the quantity of items in the cart.

* Checkout Process:
  * Begin the checkout process.
  * Enter shipping and billing information.
  * Use PayPal for payment.
  * Configure checkout to use the shipping address as the billing address.
  * Select expedited shipping methods.

* Order Review and Cancellation:
  * Review a summary of the purchase before completing checkout.
  * Cancel the order during checkout or review.
  * Edit checkout details from the review page.

* Order Notifications:
  * Provide an email address for order status notifications.
  * Receive an email with order confirmation and tracking number after the order is shipped.

#### Acceptance Criteria:
* Each story includes specific acceptance criteria that define the expected behavior.
* Stories are categorized by size (SMALL, MEDIUM) to indicate their complexity.

#### Example Stories:
* Add Items to Cart: As a shopper, I need to be able to add items to my shopping cart so I can purchase them.
* Checkout with PayPal: As a shopper, I need to be able to use PayPal on the checkout page so I can pay for my items using my PayPal account.
* Order Confirmation Email: As an e-commerce website, I need to be able to send my customers an email when an order has been confirmed.









