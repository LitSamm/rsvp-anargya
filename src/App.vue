<script setup>
import { ref, reactive, onMounted } from 'vue'
import Navbar from './components/Navbar.vue'

const markRsvpForm = reactive({
  name: '',
  email: '',
  organization: '',
  attendance: 'onsite',
  guests: 1,
  notes: '',
})

const markRsvpStatus = ref('')

function submitMarkRsvp() {
  markRsvpStatus.value = 'Thank you! The Mark 1.5 team will contact you via email.'
  markRsvpForm.name = ''
  markRsvpForm.email = ''
  markRsvpForm.organization = ''
  markRsvpForm.attendance = 'onsite'
  markRsvpForm.guests = 1
  markRsvpForm.notes = ''
}

const markUpdates = [
  {
    date: 'November 2025',
    tag: 'Energy Partner',
    title: 'Pertamina joint-lab completes safety validation',
    desc: 'Collaboration with Pertamina Drilling ensures Mark 1.5 battery pack passes runaway and thermal soak tests.',
    img: '/images/pertamina.jpg',
  },
  {
    date: 'October 2025',
    tag: 'Shakedown',
    title: 'Internal track testing session successful',
    desc: 'Dynamics team completes first braking and slalom tests with new aero package.',
    img: '/images/Rectangle 38.png',
  },
  {
    date: 'September 2025',
    tag: 'Powertrain',
    title: 'Liquid cooling battery pack ready for production',
    desc: 'Electrical subdivision completes thermal chamber validation and ready for final assembly.',
    img: '/images/Rectangle 40.png',
  },
  {
    date: 'August 2025',
    tag: 'Public Reveal',
    title: 'Mark 1.5 concept introduced at Formula-E Jakarta',
    desc: 'Anargya booth attracts over 2,000 visitors and partners with two new collaborators.',
    img: '/images/Jakarta 2022.png',
  },
]

onMounted(() => {
  const animatedItems = document.querySelectorAll('[data-animate]')
  const revealObserver = new IntersectionObserver(
    (entries, observer) => {
      entries.forEach((entry) => {
        if (entry.isIntersecting) {
          const time = entry.target.getAttribute('data-animate-delay') || 0
          entry.target.style.setProperty('--delay', `${time}ms`)
          entry.target.classList.add('is-visible')
          observer.unobserve(entry.target)
        }
      })
    },
    {
      threshold: 0.18,
      rootMargin: '0px 0px -15% 0px',
    },
  )

  animatedItems.forEach((el, index) => {
    if (!el.hasAttribute('data-animate-delay')) {
      el.setAttribute('data-animate-delay', index * 60)
    }
    revealObserver.observe(el)
  })

})
</script>

<template>
  <div class="page">
    <Navbar />
    
    <section class="hero mark-hero" data-animate data-animate-type="fade-up">
      <div class="hero-content">
        <p class="mark-eyebrow">Grand Launching 2025</p>
        <h1>Mark 1.5 — Ride The Infinity</h1>
        <p>Anargya ITS EV Team collaboration with Pertamina presents the latest Formula Student platform with a focus on energy efficiency and international competition readiness.</p>
        <div class="hero-cta">
          <a href="#rsvp" class="btn primary">RSVP Now</a>
          <a href="#overview" class="btn ghost">View Overview</a>
        </div>
      </div>
    </section>

    <section id="mark15" class="section mark-landing">
      <div class="mark-launch" data-animate data-animate-type="fade-up">
        <div class="launch-grid">
          <div class="mark-copy" data-animate data-animate-type="fade-up">
            <p class="mark-eyebrow">Grand Launching</p>
            <h2 class="section-title align-left">MARK 1.5</h2>
            <p class="section-text">
              The latest generation of Mark features a battery package from joint-development with Pertamina, active liquid cooling integration, and an immersive launch event design for partners, media, and the national EV community.
            </p>
            <ul class="mark-highlights">
              <li class="highlight-card">
                <span>Schedule</span>
                <strong>December 14, 2025</strong>
              </li>
              <li class="highlight-card">
                <span>Location</span>
                <strong>ITS Electric Vehicle Research Building</strong>
              </li>
              <li class="highlight-card">
                <span>Status</span>
                <strong>Final Assembly</strong>
              </li>
              <li class="highlight-card">
                <span>Collaborator</span>
                <strong>Pertamina Innovation Team</strong>
              </li>
            </ul>
          </div>
          <div class="mark-visual" data-animate data-animate-type="zoom">
            <img src="/images/mark 1.5.png" alt="Konsep Mark 1.5" class="mark-photo" />
            <span class="visual-caption">Render Mark 1.5</span>
          </div>
        </div>

        <div class="mark-panel mark-intro" data-animate data-animate-type="fade-up">
          <div class="intro-grid">
            <div class="intro-text">
              <p class="mark-eyebrow">Introduction</p>
              <h3>Why Mark 1.5 Matters</h3>
              <p>
                This generation increases energy efficiency by up to 12%, featuring a liquid cooling package developed with Pertamina laboratories,
                and a launch experience that specifically brings together strategic partners, media, and the national EV community.
              </p>
              <ul class="intro-list">
                <li>Ready to compete in the 2026 global Formula Student championship.</li>
                <li>Digital telemetry connected live with Pertamina booth.</li>
                <li>Cross-division team of 85+ members and industry mentors.</li>
              </ul>
            </div>
            <div class="intro-visual">
              <div class="intro-image-wrapper">
                <img src="/images/mark.JPG" alt="Mark 1.5" class="intro-image" />
              </div>
            </div>
          </div>
        </div>

        <div id="overview" class="mark-panel mark-overview" data-animate data-animate-type="fade-up">
          <div class="mark-panel-head">
            <p class="mark-eyebrow">Overview</p>
            <h3>Modular platform focused on performance & reliability</h3>
            <p>
              Mark 1.5 combines a new generation battery package, active liquid cooling system supervised by Pertamina, and digital telemetry to shorten pit sessions. Development is carried out across mechanical, electrical, non-technical divisions, and industry advisors.
            </p>
          </div>
          <div class="mark-metrics">
            <article class="metric-card">
              <span>0-60 km/h</span>
              <strong>3.3s</strong>
              <p>Target acceleration for official launch demo session.</p>
            </article>
            <article class="metric-card">
              <span>Battery Efficiency</span>
              <strong>12%</strong>
              <p>Energy density upgrade thanks to thermal optimization with Pertamina.</p>
            </article>
            <article class="metric-card">
              <span>Collaborator Team</span>
              <strong>85+</strong>
              <p>Cross-major students & Pertamina engineers directly involved.</p>
            </article>
          </div>
        </div>

        <div id="updates" class="mark-panel updates-panel" data-animate data-animate-type="fade-up">
          <div class="mark-panel-head">
            <p class="mark-eyebrow">Latest Updates</p>
            <h3>Mark 1.5 Progress Timeline</h3>
          </div>
          <div class="update-timeline">
            <article v-for="item in markUpdates" :key="item.title" class="update-card">
              <div class="update-media">
                <img :src="item.img" :alt="item.title" />
              </div>
              <div class="update-content">
                <span class="update-date">{{ item.date }} — {{ item.tag }}</span>
                <h4>{{ item.title }}</h4>
                <p>{{ item.desc }}</p>
              </div>
            </article>
          </div>
        </div>

        <div id="rsvp" class="mark-panel rsvp-panel" data-animate data-animate-type="fade-up">
          <div class="mark-panel-head">
            <p class="mark-eyebrow">Exclusive RSVP</p>
            <h3>Confirm Your Attendance at Grand Launching</h3>
            <p>Limited seating available. Register yourself and your team for access to the experience booth and exclusive pit-tour session.</p>
          </div>
          <form class="rsvp-form" @submit.prevent="submitMarkRsvp">
            <label>
              Full Name
              <input v-model="markRsvpForm.name" type="text" placeholder="Your Name" required />
            </label>
            <label>
              Email
              <input v-model="markRsvpForm.email" type="email" placeholder="email@example.com" required />
            </label>
            <label>
              Organization / Community
              <input v-model="markRsvpForm.organization" type="text" placeholder="Company / University" />
            </label>
            <div class="form-row">
              <label>
                Attendance
                <select v-model="markRsvpForm.attendance">
                  <option value="onsite">On-site Launch</option>
                  <option value="virtual">Virtual Streaming</option>
                </select>
              </label>
              <label>
                Number of Guests
                <input v-model.number="markRsvpForm.guests" type="number" min="1" max="5" />
              </label>
            </div>
            <label>
              Message
              <textarea v-model="markRsvpForm.notes" rows="3" placeholder="Special requirements, questions, etc."></textarea>
            </label>
            <button type="submit" class="btn primary">Submit RSVP</button>
            <p v-if="markRsvpStatus" class="form-status">{{ markRsvpStatus }}</p>
          </form>
        </div>
      </div>
    </section>
  </div>
</template>

