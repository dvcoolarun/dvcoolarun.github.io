---
layout: page
title: About
permalink: /about/
---
  
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Roboto+Mono:ital,wght@0,100..700;1,100..700&display=swap" rel="stylesheet">
<style>
body {
  background-color: #2b2b2b;
  color: #d4d4d4;
  font-family: "Roboto Mono", monospace;
  line-height: 1.5;
  margin: 0;
  padding: 0;
  font-size: 16px;
}

mark {
  background-color: #4a90e2;
  color: #ffffff;
  padding: 2px 4px;
  border-radius: 3px;
  font-weight: 500;
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
              background-image: url('https://avatars.githubusercontent.com/u/9693884?v=4');
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
          <div class="profile-section">
              <div class="profile-image"></div>
              <h1 class="name">Arun Kumar<span class="credentials">, <mark>MCA</mark></span></h1>
              <p class="email">arunjsdev@gmail.com</p>
          </div>
          
          <div class="title-section">
              <h2 class="job-title"><mark>Frontend Developer</mark></h2>
              <div class="social-icons">
                  <a href="tel:+917206681784" title="Phone">📞</a>
                  <a href="https://github.com/dvcoolarun" title="GitHub">🔗</a>
                  <a href="https://twitter.com/dvcoolarun" title="Twitter">🐦</a>
                  <a href="https://linkedin.com/in/arun-kumar" title="LinkedIn">💼</a>
              </div>
          </div>
          
          <div class="description">
              Motivated and versatile frontend developer with expertise in <mark>Python, React/Next, and TypeScript</mark>. 
              Bringing <mark>7+ years of experience</mark> in both <mark>B2B/B2C environments</mark> delivering web applications. 
              Proven track record in <mark>managing teams</mark> and collaborating with startups. Always looking for new 
              challenges and new technologies to learn. Experienced with the <mark>software development life cycle 
              (SDLC)</mark> utilizing various project management methodologies including <mark>Agile, Scrum and Kanban</mark>. 
              Efficient working both <mark>independently and in a team environment</mark>.
          </div>
          
          <div class="section">
              <h2 class="section-title">Skills</h2>
              
              <div class="skill-item">
                  <h3 class="skill-title">Frontend Development & Programming</h3>
                  <p class="skill-description"><mark>7+ years of experience</mark> in <mark>JavaScript, TypeScript, Python, and Node.js</mark>. Expert in building scalable web applications using <mark>React, Redux/RTK, React-Query, NextJS</mark>, and modern <mark>ES6+ features</mark>. Proficient in <mark>HTML, CSS, TailWind CSS</mark>, and responsive design principles.</p>
              </div>
              
              <div class="skill-item">
                  <h3 class="skill-title">Web Technologies & Frameworks</h3>
                  <p class="skill-description">Extensive experience with <mark>React ecosystem</mark>, <mark>GraphQL integration</mark>, <mark>Django backend development</mark>, and modern build tools. Skilled in creating <mark>component libraries</mark>, implementing <mark>CI/CD pipelines</mark>, and managing state with <mark>Redux/RTK and React-Query</mark>.</p>
              </div>
              
              <div class="skill-item">
                  <h3 class="skill-title">Testing & Database Management</h3>
                  <p class="skill-description">Expert in <mark>end-to-end testing frameworks</mark> including <mark>Cypress and Playwright</mark>. Experience with <mark>SQL databases (PostgreSQL, SQLite)</mark>, <mark>SupaBase</mark>, and ensuring high-quality code through <mark>comprehensive testing strategies</mark> and database optimization.</p>
              </div>
              
              <div class="skill-item">
                  <h3 class="skill-title">Tools & Technologies</h3>
                  <p class="skill-description"><mark>AWS Services</mark> • <mark>Git/GitHub</mark> • <mark>Linux</mark> • <mark>RESTful APIs</mark> • WordPress • <mark>Web Performance Optimization</mark> • <mark>Accessibility Standards</mark> • jQuery • Selenium/Protractor • <mark>CI/CD Pipelines</mark> • <mark>Agile Development Practices</mark></p>
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
                  
                  <p class="role-info">Frontend Developer • <mark>Dec 2024 – Present</mark></p>
                  <p class="role-description">Currently <mark>leading frontend development initiatives</mark> for e-commerce platform optimization and <mark>team management</mark> using modern web technologies.</p>
                  <ul class="achievements">
                      <li>Engineered an <mark>Item Dimensions feature with live editing and synchronization</mark>, handling both <mark>the frontend & backend</mark> using an iterative approach with stakeholders</li>
                      <li><mark>Supervised the team</mark>, enhancing efficiency through <mark>Agile practices</mark>, and overseeing the development, and maintenance of <mark>scalable frontend applications</mark></li>
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
                  
                  <p class="role-info">Frontend Developer • <mark>Dec 2018 – Dec 2024 • 6 yrs</mark></p>
                  <p class="role-description">Led frontend development for <mark>multiple startup projects</mark>, focusing on <mark>conversion optimization</mark>, <mark>component architecture</mark>, and <mark>team mentorship</mark>. Specialized in <mark>TypeScript migration</mark> and modern React development practices.</p>
                  <ul class="achievements">
                      <li>Architected a <mark>Conversion Optimization Tool</mark> that <mark>boosted conversions</mark> through data tracking, proof-of-concept to production, implementing <mark>CI/CD pipelines</mark> and rigorous testing to ensure <mark>high-quality deployments</mark></li>
                      <li>Implemented a <mark>component library</mark> for a Travel B2B product, <mark>reducing development time by 30%</mark>, improving code reuse across <mark>eight product modules</mark></li>
                      <li>Spearheaded the transition from <mark>non-type to type-safe projects</mark>, improving overall <mark>code quality and maintainability</mark> while <mark>mentoring team members</mark></li>
                      <li>Collaborated with the backend team, providing <mark>technical and API design insights</mark></li>
                  </ul>
                  <p class="tech-stack">( Tech Stack: <mark>TypeScript, Python/Django, React, ES6/JavaScript, Redux/RTK, NextJS, GraphQl, HTML, CSS, TailWind, React-Query, AWS, Cypress, Playwright, Accessibility</mark> )</p>
              </div>
              
              <div class="experience-item">
                  <div class="company-header">
                      <div class="company-logo">TI</div>
                      <div>
                          <h3 class="company-name">Times Internet</h3>
                      </div>
                  </div>
                  
                  <p class="role-info">Frontend Developer • <mark>Dec 2015 – Jun 2016 • 6 mos</mark></p>
                  <p class="role-description">Focused on developing <mark>industry-specific themes</mark> and implementing <mark>comprehensive testing frameworks</mark> for enhanced user engagement.</p>
                  <ul class="achievements">
                      <li>Developed <mark>industry-specific store themes</mark> with a <mark>modular architecture</mark>, enabling customization and <mark>reducing deployment time from days to hours</mark></li>
                      <li>Implemented <mark>end-to-end testing framework</mark> achieving <mark>85% test coverage</mark> and <mark>reducing QA cycles by 50%</mark></li>
                      <li>Revamped website flows, <mark>reducing misdirected queries</mark> and significantly <mark>enhancing user engagement</mark> on previously neglected pages</li>
                  </ul>
                  <p class="tech-stack">( Tech Stack: <mark>JavaScript, JQuery, Angular, HTML, CSS, Selenium/Protractor</mark> )</p>
              </div>
              
              <div class="experience-item">
                  <div class="company-header">
                      <div class="company-logo">HD</div>
                      <div>
                          <h3 class="company-name">Handyland Design</h3>
                      </div>
                  </div>
                  
                  <p class="role-info">Frontend Developer • <mark>Jun 2015 – Nov 2015 • 5 mos</mark></p>
                  <ul class="achievements">
                      <li>Established <mark>front-end development standards</mark> and <mark>comprehensive documentation</mark>, fostering consistency across projects</li>
                      <li>Revamped <mark>10 WordPress sites</mark> by <mark>optimizing web vitals</mark>, resulting in a <mark>40% increase in page load speed</mark> and significantly <mark>improving user engagement</mark></li>
                  </ul>
                  <p class="tech-stack">( Tech Stack: <mark>WordPress, CSS, Sketch, HTML, JavaScript, JQuery, Web Performance</mark> )</p>
              </div>
          </div>
          
          <div class="section">
              <h2 class="section-title">Education</h2>
              
              <div class="education-item">
                  <h3 class="education-title">MD University</h3>
                  <p class="education-details"><mark>Master of Computer Applications (MCA)</mark> • <mark>2013 — 2015</mark></p>
                  <p class="education-description">Focused on <mark>Computer Science Engineering</mark> with comprehensive coverage of <mark>software development principles, algorithms, and modern programming methodologies</mark>.</p>
              </div>
          </div>
          
          <div class="section">
              <h2 class="section-title">Personal Projects</h2>
              
              <div class="experience-item">
                  <span class="project-title"><mark>Web2PDF</mark></span>
                  <p class="role-info">Developer • Personal Project</p>
                  <p class="role-description">Developed a <mark>Python-based tool</mark> to convert web articles into PDF format, which <mark>gained popularity and was adopted by hundreds of users</mark>. The project demonstrates expertise in <mark>Python development, web scraping, and document processing</mark>.</p>
              </div>
          </div>
          
          <div class="section">
              <h2 class="section-title">Outside Interests</h2>
              <p class="role-description">In my free time I enjoy <mark>contributing to open source projects</mark> and building <mark>innovative web applications</mark>. I'm passionate about <mark>staying current with the latest frontend technologies</mark>, participating in <mark>developer communities</mark>, and sharing knowledge through <mark>technical writing</mark>. I also enjoy working on <mark>personal projects</mark> that explore new frameworks and development patterns, particularly in the <mark>React ecosystem and modern JavaScript development</mark>.</p>
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
