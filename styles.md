Code FOR GLASS CARDS
HTML

Copy
<!-- SVG Filter for Glass Distortion -->
<svg style="display: none">
  <filter id="glass-distortion">
    <feTurbulence type="turbulence" baseFrequency="0.008" numOctaves="2" result="noise" />
    <feDisplacementMap in="SourceGraphic" in2="noise" scale="77" />
  </filter>
</svg>

<div class="glass-card">
  <div class="glass-filter"></div>
  <div class="glass-overlay"></div>
  <div class="glass-specular"></div>
  <div class="glass-content">
    <h3>Liquid Glass Card</h3>
    <p>Modern glassmorphism with distortion effects</p>
  </div>
</div>
CSS

Copy
/* Glass Card Container */
.glass-card {
  --bg-color: rgba(255, 255, 255, 0.25);
  --highlight: rgba(255, 255, 255, 0.75);
  --text: #ffffff;
  
  position: relative;
  width: 300px;
  height: 200px;
  border-radius: 20px;
  overflow: hidden;
  box-shadow: 0 6px 24px rgba(0, 0, 0, 0.2);
}

.glass-filter,
.glass-overlay,
.glass-specular {
  position: absolute;
  inset: 0;
  border-radius: inherit;
}

.glass-filter {
  z-index: 1;
  backdrop-filter: blur(4px);
  filter: url(#glass-distortion) saturate(120%) brightness(1.15);
}

.glass-distortion-overlay {
  position: absolute;
  inset: 0;
  background: radial-gradient(circle at 20% 30%, rgba(255,255,255,0.05) 0%, transparent 80%),
              radial-gradient(circle at 80% 70%, rgba(255,255,255,0.05) 0%, transparent 80%);
  background-size: 300% 300%;
  animation: floatDistort 10s infinite ease-in-out;
  mix-blend-mode: overlay;
  z-index: 2;
  pointer-events: none;
}

@keyframes floatDistort {
  0% { background-position: 0% 0%; }
  50% { background-position: 100% 100%; }
  100% { background-position: 0% 0%; }
}


.glass-overlay {
  z-index: 2;
  background: var(--bg-color);
}

.glass-specular {
  z-index: 3;
  box-shadow: inset 1px 1px 1px var(--highlight);
}

.glass-content {
  position: relative;
  z-index: 4;
  padding: 20px;
  color: var(--text);
  text-align: center;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  height: 100%;
}

.glass-content h3 {
  margin: 0 0 10px 0;
  font-size: 24px;
  font-weight: 600;
}

.glass-content p {
  margin: 0;
  opacity: 0.8;
}

/* Dark mode styles */
@media (prefers-color-scheme: dark) {
  .glass-card {
    --bg-color: rgba(0, 0, 0, 0.25);
    --highlight: rgba(255, 255, 255, 0.15);
  }
}
JavaScript [Mouse Hover Effect]

Copy
// Add mouse movement interactivity to glass elements
document.addEventListener('DOMContentLoaded', function() {
  // Get all glass elements
  const glassElements = document.querySelectorAll('.glass-card');
  
  // Add mousemove effect for each glass element
  glassElements.forEach(element => {
    element.addEventListener('mousemove', handleMouseMove);
    element.addEventListener('mouseleave', handleMouseLeave);
  });
  
  // Handle mouse movement over glass elements
  function handleMouseMove(e) {
    const rect = this.getBoundingClientRect();
    const x = e.clientX - rect.left;
    const y = e.clientY - rect.top;
    
    // Update filter turbulence based on mouse position
    const filter = this.querySelector('filter feDisplacementMap');
    if (filter) {
      const scaleX = (x / rect.width) * 100;
      const scaleY = (y / rect.height) * 100;
      filter.setAttribute('scale', Math.min(scaleX, scaleY));
    }
    
    // Add highlight effect
    const specular = this.querySelector('.glass-specular');
    if (specular) {
      specular.style.background = `radial-gradient(
        circle at ${x}px ${y}px,
        rgba(255,255,255,0.15) 0%,
        rgba(255,255,255,0.05) 30%,
        rgba(255,255,255,0) 60%
      )`;
    }
  }
  
  // Reset effects when mouse leaves
  function handleMouseLeave() {
    const filter = this.querySelector('filter feDisplacementMap');
    if (filter) {
      filter.setAttribute('scale', '77');
    }
    
    const specular = this.querySelector('.glass-specular');
    if (specular) {
      specular.style.background = 'none';
    }
  }
});




Code FOR GLASS BUTTONS
HTML

Copy
<!-- SVG Filter for Glass Distortion -->
<svg style="display: none">
  <filter id="glass-distortion">
    <feTurbulence type="turbulence" baseFrequency="0.008" numOctaves="2" result="noise" />
    <feDisplacementMap in="SourceGraphic" in2="noise" scale="77" />
  </filter>
</svg>

<button class="glass-button">
  <div class="glass-filter"></div>
  <div class="glass-overlay"></div>
  <div class="glass-specular"></div>
  <div class="glass-content">
    <span>Liquid Glass Button</span>
  </div>
</button>
CSS

Copy
/* Glass Button Container */
.glass-button {
  --bg-color: rgba(255, 255, 255, 0.25);
  --highlight: rgba(255, 255, 255, 0.75);
  --text: #ffffff;
  
  position: relative;
  padding: 12px 24px;
  border: none;
  border-radius: 12px;
  cursor: pointer;
  overflow: hidden;
  background: transparent;
  transition: transform 0.2s ease;
  outline: none;
}

.glass-button:hover {
  transform: scale(1.05);
}

.glass-button:active {
  transform: scale(0.95);
}

.glass-filter,
.glass-overlay,
.glass-specular {
  position: absolute;
  inset: 0;
  border-radius: inherit;
}

.glass-filter {
  z-index: 1;
  backdrop-filter: blur(4px);
  filter: url(#glass-distortion) saturate(120%) brightness(1.15);
}

.glass-overlay {
  z-index: 2;
  background: var(--bg-color);
}

.glass-specular {
  z-index: 3;
  box-shadow: inset 1px 1px 1px var(--highlight);
}

.glass-content {
  position: relative;
  z-index: 4;
  color: var(--text);
  font-weight: 500;
  font-size: 16px;
}

/* Dark mode styles */
@media (prefers-color-scheme: dark) {
  .glass-button {
    --bg-color: rgba(0, 0, 0, 0.25);
    --highlight: rgba(255, 255, 255, 0.15);
  }
}
JavaScript [Mouse Hover Effect]

Copy
// Add mouse movement interactivity to glass button
document.addEventListener('DOMContentLoaded', function() {
  // Get all glass elements
  const glassElements = document.querySelectorAll('.glass-button');
  
  // Add mousemove effect for each glass element
  glassElements.forEach(element => {
    element.addEventListener('mousemove', handleMouseMove);
    element.addEventListener('mouseleave', handleMouseLeave);
  });
  
  // Handle mouse movement over glass elements
  function handleMouseMove(e) {
    const rect = this.getBoundingClientRect();
    const x = e.clientX - rect.left;
    const y = e.clientY - rect.top;
    
    
    // Add highlight effect
    const specular = this.querySelector('.glass-specular');
    if (specular) {
      specular.style.background = `radial-gradient(
        circle at ${x}px ${y}px,
        rgba(255,255,255,0.15) 0%,
        rgba(255,255,255,0.05) 30%,
        rgba(255,255,255,0) 60%
      )`;
    }
  }
  
  // Reset effects when mouse leaves
  function handleMouseLeave() {
    const filter = document.querySelector('#glass-distortion feDisplacementMap');
    if (filter) {
      filter.setAttribute('scale', '77');
    }
    
    const specular = this.querySelector('.glass-specular');
    if (specular) {
      specular.style.background = 'none';
    }
  }
});




Code FOR GLASS ICONS
HTML

Copy
<!-- SVG Filter for Glass Distortion -->
<svg style="display: none">
  <filter id="glass-distortion">
    <feTurbulence type="turbulence" baseFrequency="0.008" numOctaves="2" result="noise" />
    <feDisplacementMap in="SourceGraphic" in2="noise" scale="77" />
  </filter>
</svg>

<div class="glass-icons-grid">
  <!-- Home Icon -->
  <div class="glass-icon">
    <div class="glass-filter"></div>
    <div class="glass-overlay"></div>
    <div class="glass-specular"></div>
    <div class="glass-content">
      <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
        <path d="M3 12l2-2m0 0l7-7 7 7M5 10v10a1 1 0 001 1h3m10-11l2 2m-2-2v10a1 1 0 01-1 1h-3m-6 0a1 1 0 001-1v-4a1 1 0 011-1h2a1 1 0 011 1v4a1 1 0 001 1m-6 0h6"/></svg>
    </div>
  </div>

  <!-- Settings Icon -->
  <div class="glass-icon">
    <div class="glass-filter"></div>
    <div class="glass-overlay"></div>
    <div class="glass-specular"></div>
    <div class="glass-content">
      <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
        <path d="M12 6V4m0 2a2 2 0 100 4m0-4a2 2 0 110 4m-6 8a2 2 0 100-4m0 4a2 2 0 110-4m0 4v2m0-6V4m6 6v10m6-2a2 2 0 100-4m0 4a2 2 0 110-4m0 4v2m0-6V4"/></svg>
    </div>
  </div>

  <!-- User Icon -->
  <div class="glass-icon">
    <div class="glass-filter"></div>
    <div class="glass-overlay"></div>
    <div class="glass-specular"></div>
    <div class="glass-content">
      <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
        <path d="M16 7a4 4 0 11-8 0 4 4 0 018 0zM12 14a7 7 0 00-7 7h14a7 7 0 00-7-7z"/></svg>
    </div>
  </div>

  <!-- Bell Icon -->
  <div class="glass-icon">
    <div class="glass-filter"></div>
    <div class="glass-overlay"></div>
    <div class="glass-specular"></div>
    <div class="glass-content">
      <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
        <path d="M15 17h5l-1.405-1.405A2.032 2.032 0 0118 14.158V11a6.002 6.002 0 00-4-5.659V5a2 2 0 10-4 0v.341C7.67 6.165 6 8.388 6 11v3.159c0 .538-.214 1.055-.595 1.436L4 17h5m6 0v1a3 3 0 11-6 0v-1m6 0H9"/></svg>
    </div>
  </div>
</div>
CSS

Copy
/* Glass Icons Grid */
.glass-icons-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(64px, 1fr));
  gap: 24px;
  max-width: 400px;
  margin: 0 auto;
}

.glass-icon {
  --bg-color: rgba(255, 255, 255, 0.25);
  --highlight: rgba(255, 255, 255, 0.75);
  --icon-color: #ffffff;
  --icon-size: 64px;
  
  position: relative;
  width: var(--icon-size);
  height: var(--icon-size);
  border-radius: 16px;
  overflow: hidden;
  background: transparent;
  cursor: pointer;
  transition: transform 0.2s ease;
}

.glass-icon:hover {
  transform: scale(1.1);
}

.glass-filter,
.glass-overlay,
.glass-specular {
  position: absolute;
  inset: 0;
  border-radius: inherit;
}

.glass-filter {
  z-index: 1;
  backdrop-filter: blur(4px);
  filter: url(#glass-distortion) saturate(120%) brightness(1.15);
}

.glass-overlay {
  z-index: 2;
  background: var(--bg-color);
}

.glass-specular {
  z-index: 3;
  box-shadow: inset 1px 1px 1px var(--highlight);
}

.glass-content {
  position: relative;
  z-index: 4;
  width: 100%;
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
}

.glass-content svg {
  width: 80%;
  height: 80%;
  color: var(--icon-color);
  transition: transform 0.2s ease;
}

.glass-icon:hover .glass-content svg {
  transform: scale(0.9);
}

/* Dark mode styles */
@media (prefers-color-scheme: dark) {
  .glass-icon {
    --bg-color: rgba(0, 0, 0, 0.25);
    --highlight: rgba(255, 255, 255, 0.15);
  }
}


Code FOR GLASS NAV
HTML

Copy
<!-- SVG Filter for Glass Distortion -->
<svg style="display: none">
  <filter id="glass-distortion">
    <feTurbulence type="turbulence" baseFrequency="0.008" numOctaves="2" result="noise" />
    <feDisplacementMap in="SourceGraphic" in2="noise" scale="77" />
  </filter>
</svg>

<nav class="glass-nav">
  <div class="glass-filter"></div>
  <div class="glass-overlay"></div>
  <div class="glass-specular"></div>
  <div class="glass-content">
    <ul class="nav-list">
      <li><a href="#" class="nav-item active">Home</a></li>
      <li><a href="#" class="nav-item">About</a></li>
      <li><a href="#" class="nav-item">Services</a></li>
      <li><a href="#" class="nav-item">Contact</a></li>
    </ul>
  </div>
</nav>
CSS

Copy
/* Glass Navigation Container */
.glass-nav {
  --bg-color: rgba(255, 255, 255, 0.25);
  --highlight: rgba(255, 255, 255, 0.75);
  --text: #ffffff;
  
  position: relative;
  width: 100%;
  max-width: 600px;
  border-radius: 12px;
  overflow: hidden;
  background: transparent;
}

.glass-filter,
.glass-overlay,
.glass-specular {
  position: absolute;
  inset: 0;
  border-radius: inherit;
}

.glass-filter {
  z-index: 1;
  backdrop-filter: blur(4px);
  filter: url(#glass-distortion) saturate(120%) brightness(1.15);
}

.glass-overlay {
  z-index: 2;
  background: var(--bg-color);
}

.glass-specular {
  z-index: 3;
  box-shadow: inset 1px 1px 1px var(--highlight);
}

.glass-content {
  position: relative;
  z-index: 4;
  padding: 16px;
}

.nav-list {
  list-style: none;
  margin: 0;
  padding: 0;
  display: flex;
  justify-content: center;
  gap: 24px;
}

.nav-item {
  color: var(--text);
  text-decoration: none;
  font-weight: 500;
  font-size: 16px;
  padding: 8px 16px;
  border-radius: 8px;
  transition: background-color 0.2s ease;
}

.nav-item:hover {
  background-color: rgba(255, 255, 255, 0.1);
}

.nav-item.active {
  background-color: rgba(255, 255, 255, 0.2);
}

/* Dark mode styles */
@media (prefers-color-scheme: dark) {
  .glass-nav {
    --bg-color: rgba(0, 0, 0, 0.25);
    --highlight: rgba(255, 255, 255, 0.15);
  }
}
JavaScript

Copy
document.addEventListener('DOMContentLoaded', function() {

 // Add nav item click handler
  const navItems = document.querySelectorAll('.nav-item');
  navItems.forEach(item => {
    item.addEventListener('click', function(e) {
      e.preventDefault();
      navItems.forEach(navItem => navItem.classList.remove('active'));
      this.classList.add('active');
    });
  });
});