---
layout: page
title: About
permalink: /about/
---

<style>
  .about-container {
    display: flex;
    flex-wrap: wrap;
    align-items: center;
    gap: 2rem;
  }
  
  .about-text {
    flex: 1;
    min-width: 300px;
  }
  
  .about-image {
    flex: 1;
    min-width: 300px;
    display: flex;
    justify-content: center;
  }
  
  .profile-picture {
    max-width: 100%;
    height: auto;
    border-radius: 50%;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  }
  
  .social-links {
    margin-top: 1rem;
  }
  
  .social-icon {
    width: 32px;
    height: 32px;
    margin-right: 1rem;
  }
  
  @media (max-width: 768px) {
    .about-container {
      flex-direction: column-reverse;
    }
  }
</style>    

<div class="about-container">
  <div class="about-text">
    <h2>Hey! I'm Arun 👋</h2>
    <p>
      Welcome to my personal website! I'm a web developer with a unique blend of engineering skills and creative flair. I'm passionate about technology, freelancing, and participating in hackathons.
    </p>
    <p>
      When I'm not coding or working on projects, I enjoy organizing tech meetups to connect with fellow developers and enhance our skills. I'm also active on Twitter, so feel free to reach out!
    </p>
    <p>
      Let's collaborate and create amazing web experiences together!
    </p>
  </div>
  <div class="about-image">
    <img src="https://avatars.githubusercontent.com/u/9693884?v=4" alt="Profile Picture" class="profile-picture">
  </div>
</div>