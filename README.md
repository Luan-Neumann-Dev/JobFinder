# Job Finder
 
> A full-stack job board web application where companies can post openings and developers can search and browse available positions.
 
[![Node.js](https://img.shields.io/badge/Node.js-339933?style=for-the-badge&logo=nodedotjs&logoColor=white)](https://nodejs.org/)
[![Express](https://img.shields.io/badge/Express-000000?style=for-the-badge&logo=express&logoColor=white)](https://expressjs.com/)
[![Sequelize](https://img.shields.io/badge/Sequelize-52B0E7?style=for-the-badge&logo=sequelize&logoColor=white)](https://sequelize.org/)
[![SQLite](https://img.shields.io/badge/SQLite-003B57?style=for-the-badge&logo=sqlite&logoColor=white)](https://www.sqlite.org/)
[![Bootstrap](https://img.shields.io/badge/Bootstrap-7952B3?style=for-the-badge&logo=bootstrap&logoColor=white)](https://getbootstrap.com/)

![Project View](https://github.com/Luan-Neumann-Dev/JobFinder/assets/155394874/9ff0f3bc-44ad-41ab-aa54-9965c4235624)
![Project View](https://github.com/user-attachments/assets/530ccde7-2c70-4bbd-bfd7-3678068fa4e7)
![Project View](https://github.com/user-attachments/assets/daa7d1f2-98a3-4410-8d8d-9df25bd2dfdb)

---
 
## 🎯 About
 
Job Finder is a full-stack web application built with Node.js and Express that functions as a job board targeted at remote tech positions. Companies can submit job openings through a dedicated form, and developers can browse all listings or filter them by title using the search feature.
 
The project follows the MVC pattern — models are defined with Sequelize, routes are organized in separate files, and views are rendered server-side using Handlebars templates. It was built to put together backend concepts like routing, ORM usage, and server-side rendering in a real, end-to-end application.
 
## ✨ Key Features
 
- 📋 **Job Listings Feed** - All posted positions displayed in reverse chronological order
- 🔍 **Live Title Search** - Filter jobs by keyword using Sequelize's `Op.like` query
- ➕ **Job Submission Form** - Companies can post openings with title, description, salary, company, and contact email
- 🏷️ **New Job Badge** - Recently posted jobs are visually flagged with a "New" label
- 🔗 **Job Detail Page** - Dedicated view for each listing with full description and contact info
 
## 🛠️ Tech Stack
 
**Frontend:**
- Handlebars — Server-side templating engine for dynamic HTML rendering
- Bootstrap 4 — Responsive layout, navbar, forms, and list group components
- CSS3 — Custom styles layered on top of Bootstrap
 
**Backend:**
- Node.js — Runtime environment
- Express — HTTP server, routing, and middleware setup
- body-parser — Parsing incoming POST form data
- Sequelize — ORM for model definition and database queries
- SQLite — Lightweight file-based relational database
 
**Tools:**
- nodemon — Auto-restart during development
 
## 🚀 Quick Start
 
```bash
# Clone the repository
git clone https://github.com/Luan-Neumann-Dev/job-finder.git
 
# Navigate to project
cd job-finder
 
# Install dependencies
npm install
 
# Run the project
npm run dev
```
 
Then open your browser at **http://localhost:3000**
 
## 📁 Project Structure
 
```
job-finder/
├── app.js                  # Express app setup, middleware, DB connection, and root route
├── routes/
│   └── jobs.js             # Job-specific routes — GET add form, GET detail, POST create
├── models/
│   └── Job.js              # Sequelize model definition for the jobs table
├── db/
│   ├── connection.js       # Sequelize instance with SQLite configuration
│   └── app.db              # SQLite database file
├── views/
│   ├── layouts/
│   │   └── main.handlebars # Base HTML layout with navbar and Bootstrap CDN
│   ├── index.handlebars    # Job feed with search form and listings
│   ├── add.handlebars      # Job submission form
│   └── view.handlebars     # Individual job detail page
└── public/
    ├── css/
    │   └── styles.css      # Custom CSS
    └── img/                # Static images and banners
```
 
## 💡 Technical Highlights
 
### Dynamic Search with Sequelize `Op.like`
Instead of filtering data client-side, the search is processed server-side via a conditional Sequelize query. When a search term is present, it performs a `LIKE` query against the job title; otherwise it returns all records ordered by creation date.
 
```javascript
Job.findAll({
    where: { title: { [Op.like]: `%${search}%` } },
    order: [['createdAt', 'DESC']]
})
```
 
### MVC Separation with Express Router
Job-related routes are extracted into a dedicated router file and mounted under the `/jobs` prefix, keeping `app.js` clean and the codebase organized.
 
```javascript
// app.js
app.use('/jobs', require('./routes/jobs'));
 
// routes/jobs.js
router.get('/view/:id', (req, res) => { ... });
router.post('/add', (req, res) => { ... });
```
 
## 📚 What I Learned
 
**Technical Skills:**
- Setting up an Express server with middleware, static files, and a template engine
- Defining Sequelize models and performing ORM queries (findAll, findOne, create) with conditions and ordering
- Structuring a Node.js app with the MVC pattern using Express Router
- Rendering dynamic views server-side with Handlebars layouts and partials
 
**Best Practices:**
- Separating route logic from the main app entry point
- Using environment-aware database configuration with Sequelize
- Keeping models focused — one file per entity with clear field type definitions
 
## 🗺️ Roadmap
 
- [ ] Add authentication so only registered companies can post jobs
- [ ] Implement job editing and deletion
- [ ] Add pagination to the job listings feed
- [ ] Migrate from SQLite to PostgreSQL for production readiness
- [ ] Deploy to a cloud platform (Railway, Render, or Fly.io)
 
## 📝 Notes
 
- This is a **full-stack educational project** — no authentication is implemented yet
- The SQLite database file is included in the repo for ease of setup
- Not affiliated with any real job board platform
 
## 📄 License
 
MIT License - see LICENSE for details
 
## 👤 Author
 
**Luan Neumann**
 
- LinkedIn: [Luan-Neumann-Dev](https://www.linkedin.com/in/luan-henrique-neumann-dev/)
- GitHub: [@luan-neumann-dev](https://github.com/Luan-Neumann-Dev)
 
---
 
⭐ Found this helpful? Give it a star!
