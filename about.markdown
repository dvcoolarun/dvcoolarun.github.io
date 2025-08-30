---
layout: page
title: About
permalink: /about/
---
  
  <style>
    body {
              background-color: #2b2b2b;
              color: #d4d4d4;
              font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;
              line-height: 1.5;
              margin: 0;
              padding: 0;
              font-size: 16px;
          }
          
          .container {
              max-width: 1000px;
              margin: 0 auto;
              padding: 50px 40px;
          }
          
          .header-nav {
              display: flex;
              justify-content: space-between;
              align-items: center;
              margin-bottom: 80px;
          }
          
          .blog-title {
              font-size: 32px;
              font-weight: 300;
              color: #d4d4d4;
              text-decoration: none;
          }
          
          .nav-links {
              display: flex;
              gap: 40px;
          }
          
          .nav-links a {
              color: #d4d4d4;
              text-decoration: none;
              font-size: 18px;
              font-weight: 300;
          }
          
          .nav-links a:hover {
              text-decoration: underline;
          }
          
          .profile-section {
              text-align: center;
              margin-bottom: 60px;
          }
          
          .profile-image {
              width: 200px;
              height: 200px;
              border-radius: 50%;
              background-color: #555;
              background-image: url('data:image/svg+xml,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 200 200"><circle cx="100" cy="100" r="100" fill="%23666"/><circle cx="100" cy="80" r="30" fill="%23888"/><ellipse cx="100" cy="150" rx="50" ry="30" fill="%23888"/></svg>');
              background-size: cover;
              margin: 0 auto 30px;
          }
          
          .name {
              font-size: 64px;
              font-weight: 300;
              margin: 0;
              color: #e8e6e3;
          }
          
          .credentials {
              font-size: 24px;
              color: #888;
              margin: 0;
              font-weight: 300;
          }
          
          .email {
              font-size: 18px;
              margin: 20px 0 40px;
              color: #d4d4d4;
          }
          
          .title-section {
              display: flex;
              justify-content: space-between;
              align-items: center;
              margin-bottom: 30px;
          }
          
          .job-title {
              font-size: 40px;
              font-weight: 300;
              color: #d4d4d4;
              margin: 0;
          }
          
          .social-icons {
              display: flex;
              gap: 15px;
          }
          
          .social-icons a {
              display: inline-block;
              width: 40px;
              height: 40px;
              background-color: #555;
              border-radius: 50%;
              text-align: center;
              line-height: 40px;
              color: #d4d4d4;
              text-decoration: none;
              font-size: 16px;
          }
          
          .social-icons a:hover {
              background-color: #666;
          }
          
          .description {
              font-size: 16px;
              line-height: 1.6;
              margin-bottom: 60px;
              color: #d4d4d4;
          }
          
          .contact-section {
              text-align: center;
              margin: 60px 0;
          }
          
          .contact-title {
              font-size: 28px;
              font-weight: 300;
              color: #888;
              margin: 0;
          }
          
          .section {
              margin-bottom: 60px;
          }
          
          .section-title {
              font-size: 40px;
              font-weight: 300;
              margin-bottom: 30px;
              border-bottom: 1px solid #444;
              padding-bottom: 10px;
              color: #d4d4d4;
          }
          
          .skill-item {
              margin-bottom: 30px;
          }
          
          .skill-title {
              font-size: 18px;
              font-weight: 600;
              margin-bottom: 8px;
              color: #d4d4d4;
          }
          
          .skill-description {
              font-size: 16px;
              line-height: 1.6;
              color: #d4d4d4;
          }
          
          .experience-item {
              margin-bottom: 50px;
          }
          
          .company-header {
              display: flex;
              align-items: center;
              margin-bottom: 15px;
          }
          
          .company-logo {
              width: 60px;
              height: 60px;
              background-color: #4a90e2;
              border-radius: 8px;
              margin-right: 15px;
              display: flex;
              align-items: center;
              justify-content: center;
              font-weight: bold;
              color: white;
              font-size: 16px;
          }
          
          .company-name {
              font-size: 24px;
              font-weight: 600;
              color: #d4d4d4;
              text-decoration: underline;
              margin: 0;
          }
          
          .company-description {
              font-size: 14px;
              color: #aaa;
              margin-bottom: 15px;
              font-style: italic;
          }
          
          .role-info {
              font-size: 16px;
              font-weight: 600;
              margin-bottom: 15px;
              color: #d4d4d4;
          }
          
          .role-description {
              font-size: 16px;
              line-height: 1.6;
              margin-bottom: 15px;
              color: #d4d4d4;
          }
          
          .achievements {
              list-style: none;
              padding: 0;
              margin: 0;
          }
          
          .achievements li {
              position: relative;
              padding-left: 20px;
              margin-bottom: 12px;
              line-height: 1.6;
              font-size: 16px;
          }
          
          .achievements li:before {
              content: "•";
              position: absolute;
              left: 0;
              color: #d4d4d4;
              font-weight: bold;
          }
          
          .tech-stack {
              font-size: 14px;
              color: #888;
              margin-top: 15px;
              font-style: italic;
          }
          
          .project-title {
              font-size: 18px;
              font-weight: 600;
              color: #d4d4d4;
              text-decoration: underline;
              margin-bottom: 8px;
              display: block;
          }
          
          .education-item {
              margin-bottom: 30px;
          }
          
          .education-title {
              font-size: 20px;
              font-weight: 600;
              color: #d4d4d4;
              margin-bottom: 5px;
          }
          
          .education-details {
              font-size: 16px;
              color: #d4d4d4;
              margin-bottom: 10px;
          }
          
          .education-description {
              font-size: 16px;
              line-height: 1.6;
              color: #d4d4d4;
          }
          
          .links-list {
              list-style: none;
              padding: 0;
          }
          
          .links-list li {
              margin-bottom: 8px;
          }
          
          .links-list a {
              color: #4a90e2;
              text-decoration: none;
          }
          
          .links-list a:hover {
              text-decoration: underline;
          }
  </style>    
  
  <div class="container">
          <div class="header-nav">
              <a href="#" class="blog-title">Arun's Blog</a>
              <div class="nav-links">
                  <a href="#resume">Resume</a>
                  <a href="#blog">Blog Archive</a>
                  <a href="#bookmarks">Bookmarks</a>
              </div>
          </div>
          
          <div class="profile-section">
              <div class="profile-image"></div>
              <h1 class="name">Arun Kumar<span class="credentials">, MCA</span></h1>
              <p class="email">arunjsdev@gmail.com</p>
          </div>
          
          <div class="title-section">
              <h2 class="job-title">Frontend Developer</h2>
              <div class="social-icons">
                  <a href="tel:+917206681784" title="Phone">📞</a>
                  <a href="https://github.com/dvcoolarun" title="GitHub">🔗</a>
                  <a href="https://twitter.com/dvcoolarun" title="Twitter">🐦</a>
                  <a href="https://linkedin.com/in/arun-kumar" title="LinkedIn">💼</a>
              </div>
          </div>
          
          <div class="description">
              Motivated and versatile frontend developer with expertise in Python, React/Next, and TypeScript. 
              Bringing 7+ years of experience in both B2B/B2C environments delivering web applications. 
              Proven track record in managing teams and collaborating with startups. Always looking for new 
              challenges and new technologies to learn. Experienced with the software development life cycle 
              (SDLC) utilizing various project management methodologies including Agile, Scrum and Kanban. 
              Efficient working both independently and in a team environment.
          </div>
          
          <div class="contact-section">
              <h3 class="contact-title">Contact me</h3>
          </div>
          
          <div class="section">
              <h2 class="section-title">Skills</h2>
              
              <div class="skill-item">
                  <h3 class="skill-title">Frontend Development & Programming</h3>
                  <p class="skill-description">7+ years of experience in JavaScript, TypeScript, Python, and Node.js. Expert in building scalable web applications using React, Redux/RTK, React-Query, NextJS, and modern ES6+ features. Proficient in HTML, CSS, TailWind CSS, and responsive design principles.</p>
              </div>
              
              <div class="skill-item">
                  <h3 class="skill-title">Web Technologies & Frameworks</h3>
                  <p class="skill-description">Extensive experience with React ecosystem, GraphQL integration, Django backend development, and modern build tools. Skilled in creating component libraries, implementing CI/CD pipelines, and managing state with Redux/RTK and React-Query.</p>
              </div>
              
              <div class="skill-item">
                  <h3 class="skill-title">Testing & Database Management</h3>
                  <p class="skill-description">Expert in end-to-end testing frameworks including Cypress and Playwright. Experience with SQL databases (PostgreSQL, SQLite), SupaBase, and ensuring high-quality code through comprehensive testing strategies and database optimization.</p>
              </div>
              
              <div class="skill-item">
                  <h3 class="skill-title">Tools & Technologies</h3>
                  <p class="skill-description">AWS Services • Git/GitHub • Linux • RESTful APIs • WordPress • Web Performance Optimization • Accessibility Standards • jQuery • Selenium/Protractor • CI/CD Pipelines • Agile Development Practices</p>
              </div>
          </div>
          
          <div class="section">
              <h2 class="section-title">Experience</h2>
              
              <div class="experience-item">
                  <div class="company-header">
                      <div class="company-logo">SC</div>
                      <div>
                          <h3 class="company-name">SellCord</h3>
                      </div>
                  </div>
                  <p class="company-description">Specializes in launching and managing brands on Walmart.com.</p>
                  
                  <p class="role-info">Frontend Developer • Dec 2024 – Present</p>
                  <p class="role-description">Currently leading frontend development initiatives for e-commerce platform optimization and team management using modern web technologies.</p>
                  <ul class="achievements">
                      <li>Engineered an Item Dimensions feature with live editing and synchronization, handling both the frontend & backend using an iterative approach with stakeholders</li>
                      <li>Supervised the team, enhancing efficiency through Agile practices, and overseeing the development, and maintenance of scalable frontend applications</li>
                  </ul>
              </div>
              
              <div class="experience-item">
                  <div class="company-header">
                      <div class="company-logo">AD</div>
                      <div>
                          <h3 class="company-name">Adziny</h3>
                      </div>
                  </div>
                  <p class="company-description">Digital company with a primary focus on building software solutions for startups.</p>
                  
                  <p class="role-info">Frontend Developer • Dec 2018 – Dec 2024 • 6 yrs</p>
                  <p class="role-description">Led frontend development for multiple startup projects, focusing on conversion optimization, component architecture, and team mentorship. Specialized in TypeScript migration and modern React development practices.</p>
                  <ul class="achievements">
                      <li>Architected a Conversion Optimization Tool that boosted conversions through data tracking, proof-of-concept to production, implementing CI/CD pipelines and rigorous testing to ensure high-quality deployments</li>
                      <li>Implemented a component library for a Travel B2B product, reducing development time by 30%, improving code reuse across eight product modules</li>
                      <li>Spearheaded the transition from non-type to type-safe projects, improving overall code quality and maintainability while mentoring team members</li>
                      <li>Collaborated with the backend team, providing technical and API design insights</li>
                  </ul>
                  <p class="tech-stack">( Tech Stack: TypeScript, Python/Django, React, ES6/JavaScript, Redux/RTK, NextJS, GraphQl, HTML, CSS, TailWind, React-Query, AWS, Cypress, Playwright, Accessibility )</p>
              </div>
              
              <div class="experience-item">
                  <div class="company-header">
                      <div class="company-logo">TI</div>
                      <div>
                          <h3 class="company-name">Times Internet</h3>
                      </div>
                  </div>
                  
                  <p class="role-info">Frontend Developer • Dec 2015 – Jun 2016 • 6 mos</p>
                  <p class="role-description">Focused on developing industry-specific themes and implementing comprehensive testing frameworks for enhanced user engagement.</p>
                  <ul class="achievements">
                      <li>Developed industry-specific store themes with a modular architecture, enabling customization and reducing deployment time from days to hours</li>
                      <li>Implemented end-to-end testing framework achieving 85% test coverage and reducing QA cycles by 50%</li>
                      <li>Revamped website flows, reducing misdirected queries and significantly enhancing user engagement on previously neglected pages</li>
                  </ul>
                  <p class="tech-stack">( Tech Stack: JavaScript, JQuery, Angular, HTML, CSS, Selenium/Protractor )</p>
              </div>
              
              <div class="experience-item">
                  <div class="company-header">
                      <div class="company-logo">HD</div>
                      <div>
                          <h3 class="company-name">Handyland Design</h3>
                      </div>
                  </div>
                  
                  <p class="role-info">Frontend Developer • Jun 2015 – Nov 2015 • 5 mos</p>
                  <ul class="achievements">
                      <li>Established front-end development standards and comprehensive documentation, fostering consistency across projects</li>
                      <li>Revamped 10 WordPress sites by optimizing web vitals, resulting in a 40% increase in page load speed and significantly improving user engagement</li>
                  </ul>
                  <p class="tech-stack">( Tech Stack: WordPress, CSS, Sketch, HTML, JavaScript, JQuery, Web Performance )</p>
              </div>
          </div>
          
          <div class="section">
              <h2 class="section-title">Education</h2>
              
              <div class="education-item">
                  <h3 class="education-title">MD University</h3>
                  <p class="education-details">Master of Computer Applications (MCA) • 2013 — 2015</p>
                  <p class="education-description">Focused on Computer Science Engineering with comprehensive coverage of software development principles, algorithms, and modern programming methodologies.</p>
              </div>
          </div>
          
          <div class="section">
              <h2 class="section-title">Personal Projects</h2>
              
              <div class="experience-item">
                  <span class="project-title">Web2PDF</span>
                  <p class="role-info">Developer • Personal Project</p>
                  <p class="role-description">Developed a Python-based tool to convert web articles into PDF format, which gained popularity and was adopted by hundreds of users. The project demonstrates expertise in Python development, web scraping, and document processing.</p>
              </div>
          </div>
          
          <div class="section">
              <h2 class="section-title">Outside Interests</h2>
              <p class="role-description">In my free time I enjoy contributing to open source projects and building innovative web applications. I'm passionate about staying current with the latest frontend technologies, participating in developer communities, and sharing knowledge through technical writing. I also enjoy working on personal projects that explore new frameworks and development patterns, particularly in the React ecosystem and modern JavaScript development.</p>
          </div>
          
          <div class="section">
              <h2 class="section-title">Additional Links</h2>
              <ul class="links-list">
                  <li>LinkedIn: <a href="https://linkedin.com/in/arun-kumar">linkedin.com/in/arun-kumar</a></li>
                  <li>GitHub: <a href="https://github.com/dvcoolarun">github.com/dvcoolarun</a></li>
                  <li>Email: <a href="mailto:arunjsdev@gmail.com">arunjsdev@gmail.com</a></li>
                  <li>Phone: <a href="tel:+917206681784">+91 7206681784</a></li>
              </ul>
          </div>
      </div>
