# Twitter-Mini Part 1 Functionality Checklist

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
