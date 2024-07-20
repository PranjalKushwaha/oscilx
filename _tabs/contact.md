---
# the default layout is 'page'
# icon: fas fa-info-circle
order: 6
--- 
<style>
  .hero-content {
    position: relative;
    /* background-image: url('/assets/images/trace.png'); */
    background-image: url("/assets/images/pcb2.svg");
    background-size: 100%;
    background-position: center center;
    background-repeat: no-repeat;
    padding: 50px 0;
    text-align: center;

  }

  .hero-content img{
    position: center center;
    display: inline-block;
    padding: 10px;
    margin: 10px 0;
    color: blue;
    font-weight: bolder;
    text-shadow: 0 0 1px rgb(0, 0, 255);
  }

  .hero-content img {
    font-size: 2.8rem;
    transform: translate(0%, -0%) scale(1.5);
  }
</style>

<style>
  .contact-icons {
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 80px;
    margin: 50px 0;
  }
  .contact-icons a {
    font-size: 30px;
    color: #0000ff
    transition: color 0.3s ease;
  }
  .contact-icons a:hover {
    color: #0077b5;
  }
</style>


<div class="hero-content">
  <div class="blur-background"></div>
  <div class="content-wrapper">
     <img src="/assets/images/logo.svg">
     
  </div>
</div>
<div class="contact-icons">
  <!-- <a href="https://www.linkedin.com/in/yourprofile" target="_blank" rel="noopener noreferrer">
    <i class="fab fa-linkedin"></i>
  </a> -->
  <a href="mailto:pranjal@oscilx.com">
    <i class="fas fa-envelope"></i>
  </a>
  <a href="tel:+918448933647">
    <i class="fas fa-phone"></i>
  </a>
</div>