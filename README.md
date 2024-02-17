# Mini-Twitter Functionality Checklist

## Phase 1: Project Setup and Database Design
- [ ] Set up development environment (IDE, database, etc.)
- [ ] Create a GitHub repository for version control
- [ ] Design database schema
  - [ ] Define `User` entity with attributes (id, username, email, password, etc.)
  - [ ] Define `Post` entity with attributes (id, user_id, content, timestamp)
  - [ ] Define `Followers` relationship (user_id, follower_id)

## Phase 2: Backend Development - Basic Features
### User Authentication
- [ ] Implement user registration
  - [ ] Collect user data (username, email, password)
  - [ ] Validate data (unique email, password criteria, etc.)
  - [ ] Encrypt password before saving to database
  - [ ] Return success or error message
- [ ] Implement user login
  - [ ] Verify email/password
  - [ ] Generate authentication token (JWT)
  - [ ] Return token and user details
- [ ] Implement middleware for authentication token verification

### Testing: User Authentication
- [ ] Write unit tests for registration
- [ ] Write unit tests for login
- [ ] Write unit tests for middleware authentication

## Phase 3: Backend Development - Core Features
### Posts Management
- [ ] API to create a post
  - [ ] Ensure user is authenticated
  - [ ] Validate post content
  - [ ] Save post to database
  - [ ] Return post details
- [ ] API to view a user's posts
  - [ ] Retrieve and return posts by user_id
- [ ] API to delete a post
  - [ ] Ensure user is authenticated and owns the post
  - [ ] Delete post from database

### User Relationships
- [ ] API to follow another user
  - [ ] Ensure user is authenticated
  - [ ] Update `Followers` relationship in database
- [ ] API to unfollow another user
  - [ ] Ensure user is authenticated
  - [ ] Remove `Followers` relationship from database
- [ ] API to list followers and following
  - [ ] Retrieve and return users following and followed by a user

### Testing: Core Features
- [ ] Write unit tests for creating, viewing, and deleting posts
- [ ] Write unit tests for following/unfollowing users
- [ ] Write unit tests for listing followers and following

## Phase 4: Frontend Development (Optional)
- [ ] Set up frontend project structure
- [ ] Implement login page
  - [ ] Form for email/password input
  - [ ] Submit form and handle response
- [ ] Implement registration page
  - [ ] Form for username, email, password input
  - [ ] Submit form and handle response
- [ ] Implement main feed
  - [ ] Display logged-in user's posts
  - [ ] Option to create new posts
- [ ] Implement user profile page
  - [ ] Display user information and posts
  - [ ] Follow/unfollow button and functionality

## Phase 5: Integration and Testing
- [ ] Ensure frontend communicates correctly with backend APIs
- [ ] Perform integration testing
- [ ] Conduct user acceptance testing (UAT)

## Phase 6: Documentation and Deployment
- [ ] Document the API endpoints
- [ ] Document the database schema
- [ ] Deploy the application to a cloud service

# Future Plan Checklist for Mini-Twitter Application

## Phase 1: Enhancements to Core Features
- [ ] **Likes for Posts:**
  - [ ] Implement a `Like` model in the Node.js backend to track likes on posts.
  - [ ] Create API endpoints for liking/unliking a post, ensuring to update the likes count dynamically.

- [ ] **Basic User Profile Settings:**
  - [ ] Allow users to update their profile information such as username, bio, and email through a dedicated API endpoint.
  - [ ] Implement file upload functionality for profile pictures, considering image storage and retrieval strategies.

## Phase 2: Introduction to Elasticsearch
- [ ] **Setup Elasticsearch:**
  - [ ] Install Elasticsearch and integrate it with the Node.js application.
  - [ ] Familiarize with Elasticsearch concepts such as indices, documents, and mappings.

- [ ] **Indexing Posts:**
  - [ ] Design and create an Elasticsearch index for posts, ensuring to define appropriate mappings for efficient searching.
  - [ ] Implement backend logic to index new posts, update existing ones, and delete as necessary.

- [ ] **Search Functionality:**
  - [ ] Develop an API endpoint for keyword search in posts, leveraging Elasticsearch's full-text search capabilities.
  - [ ] Integrate search functionality in the UI if a frontend is being developed.

### Elasticsearch Tips:
- **Use Analyzers:** Customize analyzers in Elasticsearch to improve search results based on the specific needs of your application (e.g., lowercase filters, stop words).
- **Test Different Queries:** Experiment with various query types (match, term, bool, etc.) to achieve the desired search precision and recall.
- **Monitor Performance:** Utilize Elasticsearch's monitoring tools to observe query performance and adjust indices/mappings accordingly.

## Phase 3: Stress Testing, Optimization, and Deployment
- [ ] **Node.js-specific Stress Testing Tools:**
  - [ ] Explore and use stress testing tools such as `Artillery` or `k6`. These tools are well-suited for testing Node.js applications, allowing you to simulate high traffic and analyze the app's performance.
  - [ ] Implement test scripts to simulate various scenarios (user login, posting, searching) and analyze throughput, latency, and error rates.

- [ ] **Analysis and Optimization:**
  - [ ] Based on stress testing results, identify bottlenecks (e.g., slow database queries, inefficient API endpoints).
  - [ ] Optimize by implementing caching, refining database queries, or adjusting server configurations.

- [ ] **Deployment on AWS:**
  - [ ] Use Terraform or AWS CloudFormation to define and manage infrastructure as code. This allows for the automated setup of required AWS services (EC2 instances, RDS for databases, S3 for storage, etc.).
  - [ ] Automate application deployment using Ansible. Create Ansible playbooks to configure AWS instances, deploy the Node.js application, and ensure dependencies are installed.

### AWS Deployment Tips:
- **Automate Everything:** Use Ansible for configuration management and Terraform/CloudFormation for infrastructure provisioning to make deployment and scaling more efficient.
- **Secure Your Setup:** Always use AWS IAM roles and policies to manage access to AWS resources securely. Utilize security groups to control access to EC2 instances.
- **Monitor and Scale:** Leverage AWS CloudWatch for monitoring application performance and set up auto-scaling to adjust resources based on demand.

## Additional Notes:
- **Version Control:** Regularly commit and document changes in GitHub to track the evolution of the project and facilitate collaboration.
- **Continuous Learning:** Encourage the exploration of official documentation and community resources for deeper insights into Node.js, Elasticsearch, Ansible, Terraform/CloudFormation, and AWS services.
- **Community and Support:** Utilize forums, Stack Overflow, and other community platforms for support and to share knowledge gained throughout the project.

This enhanced plan aims to provide a comprehensive learning journey, from application development with Node.js to deploying and managing infrastructure on AWS, along with introducing essential DevOps practices. The inclusion of stress testing and Elasticsearch tips ensures the student gains practical insights into optimizing application performance and search capabilities.

