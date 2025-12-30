<script>
  export default {
    name: 'App',
    data() {
      return {
        currentYear: new Date().getFullYear(),
        profile: {
          name: 'Rohan.M.Nair',
          eyebrow: 'Engineer • Research • Robotics',
          subtitle: 'BS CS @ Georgia Tech • Building across web, robotics, and simulation.',
          about: 'I design and build systems that bridge the physical and digital worlds — from full‑stack web to robotics and simulation workflows.'
        },
        education: [
          { 
            school: 'Georgia Institute of Technology',
            period: '2023 — Present',
            credential: 'Bachelor of Science in Computer Science',
            location: 'Atlanta, GA'
          },
        ],
        experience: [
          {
            title: 'Application Engineer Intern',
            org: 'Waystar',
            period: 'May 2025 — Present',
            tags: ['LLMs', 'Healthcare', 'Vertex AI'],
            bullets: [
              'Researching and integrating LLMs with Google Vertex AI to develop a custom code copilot for internal software.',
              'Modernizing legacy systems supporting over 1,000,000 unique healthcare providers.',
              'Developed a PayPal integration to streamline transactions for enterprise clients.'
            ]
          },
          {
            title: 'Undergraduate Research Assistant',
            org: 'Georgia Institute of Technology',
            period: 'Jan 2024 — May 2025',
            tags: ['Machine Learning', 'Computer Vision', 'FEA'],
            bullets: [
              'Leveraging machine learning for Finite Element Analysis (FEA) on varied 3D models to improve simulation efficiency.',
              'Built computer vision models (CNNs) to detect and classify manufacturing defects.',
              'Collaborating with faculty to help establish AI minor programs at Georgia Tech.'
            ]
          },
          {
            title: 'Robotics Intern',
            org: 'Automation Direct',
            period: 'Summer 2024',
            tags: ['Robotics', 'Automation', 'Python'],
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
            featured: true,
            description: 'Community-assisted lost item recovery app.',
            bullets: [
              'AI-powered image matching via OpenAI CLIP embeddings and FAISS.',
              'FastAPI backend with MySQL and Docker; secure auth with bcrypt + JWT.'
            ],
            links: { primary: 'https://github.com/vedantlbhatt/TrackMy' },
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
      ,
      mouseX: 0,
      mouseY: 0
      };
    },
    methods: {
      requestInfo(project) {
        alert(`${project.title}: Enterprise project. Summary and redacted case study available on request.`);
      },
      handleHeroMove(e) {
        // Simple parallax calculation
        const x = (e.clientX - window.innerWidth / 2) / 25;
        const y = (e.clientY - window.innerHeight / 2) / 25;
        this.mouseX = x;
        this.mouseY = y;
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
        <section class="hero container" @mousemove="handleHeroMove">
          <div class="hero-copy">
            <div class="eyebrow">{{ profile.eyebrow }}</div>
            <h1>{{ profile.name }}</h1>
            <p class="subtitle">{{ profile.subtitle }}</p>
            <div class="cta-row">
              <a class="btn primary" href="#projects">View Projects</a>
              <a class="btn ghost" href="#contact">Get in Touch</a>
            </div>
          </div>
          <div class="hero-divider"></div>
          <div class="hero-art" aria-hidden="true">
            <div class="art-label">Robotics · Simulation · Web</div>
            <div class="orb orb-a" :style="{ transform: `translate(${mouseX}px, ${mouseY}px)` }"></div>
            <div class="orb orb-b" :style="{ transform: `translate(${-mouseX}px, ${-mouseY}px)` }"></div>
            <div class="grid-overlay"></div>
          </div>
        </section>
  
        <section id="about" class="section container">
          <div class="section-eyebrow">Overview</div>
          <h2>About</h2>
          <p class="lead">{{ profile.about }}</p>
        </section>

        <section id="skills" class="section container">
          <div class="section-eyebrow">Expertise</div>
          <h2>Skills & Tools</h2>
          <div style="display: flex; flex-wrap: wrap; gap: 0.5rem; margin-top: 1.5rem;">
            <span v-for="skill in skills" :key="skill" class="tag">{{ skill }}</span>
          </div>
        </section>
  
        <section id="education" class="section container">
          <div class="section-eyebrow">Education</div>
          <h2>Georgia Tech</h2>
          <div class="timeline">
            <article class="card education-card" v-for="(ed, idx) in education" :key="idx">
              <div class="card-head">
                <h3>{{ ed.school }}</h3>
                <span class="badge">{{ ed.period }}</span>
              </div>
              <p>{{ ed.credential }}<span v-if="ed.credential && ed.location"> — </span>{{ ed.location }}</p>
            </article>
          </div>
        </section>
  
        <section id="experience" class="section container">
          <div class="section-eyebrow">Timeline</div>
          <h2>Experience</h2>
          <div class="timeline">
            <article class="card" v-for="(item, idx) in experience" :key="idx">
              <div class="card-head">
                <h3>{{ item.title }}</h3>
                <span class="badge">{{ item.org }}</span>
              </div>
              <div class="card-tags">
                <span v-for="tag in item.tags" :key="tag" class="tag">{{ tag }}</span>
              </div>
              <div class="card-period">{{ item.period }}</div>
              <ul class="card-bullets">
                <li v-for="(bullet, i) in item.bullets" :key="i">
                  <span class="bullet-icon"></span>
                  {{ bullet }}
                </li>
              </ul>
            </article>
          </div>
        </section>
  
        <section id="projects" class="section container">
          <div class="section-eyebrow">Featured Work</div>
          <h2>Projects</h2>
          <div class="projects-grid">
            <article 
              class="card project" 
              :class="{ 'featured-project': project.featured }"
              v-for="(project, idx) in projects" 
              :key="idx"
            >
              <div class="card-head">
                <h3>{{ project.title }}</h3>
                <span class="tag" :class="{ enterprise: project.enterprise }">{{ project.tag }}</span>
              </div>
              <p>{{ project.description }}</p>
              <ul class="card-bullets">
                <li v-for="(b, i) in project.bullets" :key="i">
                  <span class="bullet-icon"></span>
                  {{ b }}
                </li>
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
          <div class="section-eyebrow">Connect</div>
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
  