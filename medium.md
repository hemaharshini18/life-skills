# WriteSphere (Medium Clone) - User Personas, User Stories & ER Diagram

---

##  Ananya Verma (Blogger / Author)

**Role:** Content Creator (Primary)  
**Age:** 29  
**Occupation:** Independent Writer & Tech Blogger  
**Location:** Bengaluru, India  
**Tech Comfort Level:** High — experienced with online publishing tools  
**Devices:** Laptop and Tablet  

### Overview
Ananya writes in-depth articles and wants a platform that allows her to **create, organize, and manage content** efficiently. She values engagement analytics and the ability to interact with her audience.  

### Core Features
- **Authentication:** Sign up, login, secure password management.  
- **Profile Management:** Update username, email, and bio (linked to USER table).  
- **Post Management:** Create, edit, delete posts (POST table).  
- **Comment Moderation:** Manage comments on her posts (COMMENT table).  
- **Likes & Engagement:** Track likes on posts (LIKE table).  

### User Stories
- As blogger **ISBAT** sign up and log in securely so I can manage my content.  
- As blogger **ISBAT** create a post with title and content so I can share my thoughts.  
- As blogger **ISBAT** edit or delete my posts so I can keep my content updated.  
- As blogger **ISBAT** moderate comments on my posts so I can maintain meaningful discussions.  
- As blogger **ISBAT** view likes for my posts so I can track engagement.  
- As blogger **ISBAT** update my profile information so readers know about me.  

---

##  Ravi Patel (Reader / Consumer)

**Role:** Content Consumer  
**Age:** 24  
**Occupation:** College Student  
**Location:** Hyderabad, India  
**Tech Comfort Level:** Medium — prefers mobile-first, simple interfaces  
**Devices:** Smartphone primarily  

### Overview
Ravi enjoys discovering and interacting with blogs. He wants an intuitive interface to **read, comment, like, and follow authors**.  

### Core Features
- **Feed & Discovery:** Browse posts from followed authors (USER ↔ POST).  
- **Search:** Find posts by title or content (POST).  
- **Comments:** Engage with authors by commenting (COMMENT table).  
- **Likes:** Like posts to show appreciation (LIKE table).  
- **Follow Authors:** Follow authors to personalize feed (FOLLOW table).  

### User Stories
- As reader **ISBAT** sign up and log in so I can interact with posts.  
- As reader **ISBAT** browse posts by authors so I can find content of interest.  
- As reader **ISBAT** like posts so I can show appreciation for quality content.  
- As reader **ISBAT** comment on posts so I can participate in discussions.  
- As reader **ISBAT** follow authors so I can see their new posts in my feed.  
- As reader **ISBAT** search for posts using keywords so I can discover new content.  

---

## [ER Diagram](https://www.mermaidchart.com/d/46ac9b12-d7e6-465e-8afa-0122b3b13546)
