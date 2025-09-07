<script>
export default {
  name: 'App',
  data() {
    return {
      currentYear: new Date().getFullYear(),
      profile: {
        name: 'Rohan .M. Nair',
        eyebrow: 'Engineer • Research • Robotics',
        subtitle: 'BS CS @ Georgia Tech • Building across web, robotics, and simulation.',
        about: 'I design and build systems that bridge the physical and digital worlds — from full‑stack web to robotics and simulation workflows.'
      },
      education: [
        { school: 'Georgia Institute of Technology' },
      ],
      experience: [
        {
          title: 'Application Engineer Intern',
          org: 'Waystar',
          bullets: [
            'Researching and integrating LLMs with Google Vertex AI to develop a custom code copilot for internal software.',
            'Modernizing legacy systems supporting over 1,000,000 unique healthcare providers.',
            'Developed a PayPal integration to streamline transactions for enterprise clients.'
          ]
        },
        {
          title: 'Undergraduate Research Assistant',
          org: 'Georgia Institute of Technology',
          bullets: [
            'Leveraging machine learning for Finite Element Analysis (FEA) on varied 3D models to improve simulation efficiency.',
            'Built computer vision models (CNNs) to detect and classify manufacturing defects.',
            'Collaborating with faculty to help establish AI minor programs at Georgia Tech.'
          ]
        },
        {
          title: 'Robotics Intern',
          org: 'Automation Direct',
          bullets: [
            'Maintained and optimized robotic applications to ensure uninterrupted production workflows.',
            'Automated analysis of tote performance data using Excel macros, boosting throughput.',
            'Developed a Python script to capture and store 100+ daily tote images with barcode metadata to an FTP server.'
          ]
        }
      ],
      projects: [
        {
          title: 'Track My',
          tag: 'Mobile',
          enterprise: false,
          description: 'Community-assisted lost item recovery app.',
          bullets: [
            'AI-powered image matching via OpenAI CLIP embeddings and FAISS.',
            'FastAPI backend with MySQL and Docker; secure auth with bcrypt + JWT.'
          ],
          links: { primary: '#' },
          note: 'In development'
        },
        {
          title: 'Robotic Control Web Application',
          tag: 'Web',
          enterprise: false,
          description: 'Real-time monitoring and management for three robotic systems.',
          bullets: [
            'Vue.js front end with PrimeVue; Axios integration to WMS for live updates.',
            'Error reporting and barcode scanning workflows wired to a Java/Spring backend.'
          ],
          links: {},
          note: 'Demo on request'
        },
        {
          title: 'Cognitive Engineering Chatbot',
          tag: 'Research',
          enterprise: false,
          description: 'Decision-support bot integrating CFD with numerical optimization for server-stack cooling.',
          bullets: [
            'Implemented L-BFGS-B to optimize inlet velocity under constraints.',
            'Reduced computational cost while maintaining simulation accuracy.'
          ],
          links: {},
          note: 'Accepted at IEOM 2025 (Singapore)'
        },
        {
          title: 'ServerStacks',
          tag: 'Python',
          enterprise: false,
          description: 'Server and stack automation toolkit in Python.',
          links: { primary: 'https://github.com/rohanprofessional-1/ServerStacks' }
        },
        {
          title: 'Orthapedic-Scaffold-ML-FEA',
          tag: 'Python',
          enterprise: false,
          description: 'ML-driven analysis of orthopedic scaffold structures with FEA workflows.',
          links: { primary: 'https://github.com/rohanprofessional-1/Orthapedic-Scaffold-ML-FEA' }
        }
      ],
      contactLinks: [
        { label: 'LinkedIn', href: 'https://www.linkedin.com/in/rohan-nair-489662327', rel: 'noopener noreferrer', target: '_blank' },
        { label: 'GitHub', href: 'https://github.com/rohanprofessional-1', rel: 'noopener noreferrer', target: '_blank' },
        { label: 'Resume', href: '/Rohan_M_Nair_Resume.pdf', rel: 'noopener noreferrer', target: '_blank' }
      ],
      skills: [
        'Java', 'Python', 'C++', 'JavaScript', 'TypeScript', 'PHP', 'SQL', 'HTML/CSS',
        'Vue.js', 'React', 'FastAPI', 'Flask', 'Spring', 'JUnit', 'Axios', 'PrimeVue', 'ROS',
        'Docker', 'Git', 'GitHub', 'GitLab', 'Postman', 'VS Code', 'PyCharm', 'IntelliJ',
        'Pandas', 'NumPy', 'OpenCV', 'DepthAI', 'PyTorch', 'PhotonVision', 'Scikit-learn', 'Streamlit'
      ]
    };
  },
  methods: {
    requestInfo(project) {
      alert(`${project.title}: Enterprise project. Summary and redacted case study available on request.`);
    }
  }
}
</script>

<template>
  <div>
    <header class="site-header">
      <div class="container header-inner">
        <a class="brand" href="#">RMN</a>
        <nav class="nav">
          <a href="#about">About</a>
          <a href="#experience">Experience</a>
          <a href="#projects">Projects</a>
          <a href="#contact">Contact</a>
        </nav>
      </div>
    </header>

    <main>
      <section class="hero container">
        <div class="hero-copy">
          <div class="eyebrow">{{ profile.eyebrow }}</div>
          <h1>{{ profile.name }}</h1>
          <p class="subtitle">{{ profile.subtitle }}</p>
          <div class="cta-row">
            <a class="btn primary" href="#projects">View Projects</a>
            <a class="btn ghost" href="#contact">Get in Touch</a>
          </div>
        </div>
        <div class="hero-art" aria-hidden="true">
          <div class="orb orb-a"></div>
          <div class="orb orb-b"></div>
          <div class="grid-overlay"></div>
        </div>
      </section>

      <section id="about" class="section container">
        <h2>About</h2>
        <p class="lead">{{ profile.about }}</p>
      </section>

      <section id="education" class="section container" v-if="education && education.length">
        <h2>Education</h2>
        <div class="timeline">
          <article class="card" v-for="(ed, idx) in education" :key="idx">
            <div class="card-head">
              <h3>{{ ed.school }}</h3>
              <span class="badge" v-if="ed.period">{{ ed.period }}</span>
            </div>
            <p v-if="ed.credential || ed.location">{{ ed.credential }}<span v-if="ed.credential && ed.location"> — </span>{{ ed.location }}</p>
          </article>
        </div>
      </section>

      <section id="experience" class="section container">
        <h2>Experience</h2>
        <div class="timeline">
          <article class="card" v-for="(item, idx) in experience" :key="idx">
            <div class="card-head">
              <h3>{{ item.title }}</h3>
              <span class="badge">{{ item.org }}</span>
            </div>
            <div style="display:flex;align-items:center;gap:12px;min-height:56px;">
              <img v-if="item.logo" :src="item.logo" :alt="item.org + ' logo'" style="height:40px;width:auto;filter:brightness(1.1) contrast(1.1) drop-shadow(0 0 10px rgba(59,130,246,0.25));" />
            </div>
          </article>
        </div>
      </section>

      <section id="projects" class="section container">
        <h2>Projects</h2>
        <div class="projects-grid">
          <article class="card project" v-for="(project, idx) in projects" :key="idx">
            <div class="card-head">
              <h3>{{ project.title }}</h3>
              <span class="tag" :class="{ enterprise: project.enterprise }">{{ project.tag }}</span>
            </div>
            <p>{{ project.description }}</p>
            <ul v-if="project.bullets && project.bullets.length">
              <li v-for="(b, i) in project.bullets" :key="i">{{ b }}</li>
            </ul>
            <div class="actions">
              <a v-if="project.links && project.links.primary" class="btn small primary" :href="project.links.primary">Open</a>
              <a v-if="project.links && project.links.caseStudy" class="btn small ghost" :href="project.links.caseStudy">Case Study</a>
              <button v-if="project.enterprise" class="btn small ghost" @click="requestInfo(project)">Summary only</button>
              <span v-if="project.note" class="note">{{ project.note }}</span>
            </div>
          </article>
        </div>
      </section>

      <section id="contact" class="section container">
        <h2>Contact</h2>
        <div class="contact-cards">
          <a v-for="(link, idx) in contactLinks" :key="idx" class="card link-card" :href="link.href" :rel="link.rel" :target="link.target || null">{{ link.label }}</a>
        </div>
      </section>
    </main>

    <footer class="site-footer container">
      <span>© {{ currentYear }} {{ profile.name }}</span>
      <span class="dot">•</span>
      <span>Made with care</span>
    </footer>
  </div>
</template>

<style scoped>
/* Component-scoped tweaks, if needed */
</style>
