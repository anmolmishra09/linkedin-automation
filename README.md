LinkedIn Automation System
A sophisticated browser automation framework for LinkedIn with advanced anti-detection techniques, human-like behavior simulation, and clean Go architecture.
⚠️ Important Disclaimer
This project is a technical proof-of-concept for educational purposes only. Automated interaction with LinkedIn may violate their Terms of Service. Use at your own risk and always respect platform policies and rate limits.
🎯 Features
Core Automation

Profile Visiting: Automated profile viewing with human-like scrolling and interaction
Search Automation: Automated people/company search (extensible)
Connection Management: Automated connection requests with personalized messages (extensible)
Data Extraction: Profile information scraping with structured output

Anti-Detection Techniques

WebDriver Detection Bypass: Removes all automation fingerprints
Canvas Fingerprinting Protection: Adds realistic variance to canvas signatures
Browser Fingerprint Randomization: Randomizes browser characteristics
Audio Context Masking: Prevents audio fingerprinting
WebGL Fingerprint Spoofing: Mimics realistic GPU signatures
Timing Attack Prevention: Adds variance to timing measurements
Plugin & Language Spoofing: Realistic browser environment simulation

Human-Like Behavior

Natural Scrolling: Variable scroll speeds with easing
Mouse Movement Simulation: Bezier curve-based realistic mouse paths
Typing Simulation: Variable typing speeds with thinking pauses
Reading Time Calculation: Realistic page interaction timing
Random Pauses: Human-like breaks and delays
Viewport Variation: Random but realistic viewport sizes

Architecture

Clean Separation of Concerns: Modular design with clear responsibilities
Context-Based Cancellation: Graceful shutdown handling
Configuration Management: Environment-based configuration
Error Handling: Comprehensive error handling and logging
Extensible Design: Easy to add new automation workflows

🚀 Quick Start
Prerequisites

Go 1.21+ installed
Chrome/Chromium browser installed
Git for cloning the repository

Installation
bash# Clone the repository
git clone <your-repo-url>
cd linkedin-automation

# Install dependencies
go mod download

# Copy environment configuration
cp .env.example .env

# Edit .env with your preferences
nano .env
Basic Usage
bash# Visit a LinkedIn profile (with browser visible for first-time login)
go run . -profile "https://www.linkedin.com/in/anmolmishra09/" -mode profile

# Run in headless mode (after initial login)
go run . -profile "https://www.linkedin.com/in/anmolmishra09/" -mode profile -headless

# Search mode (to be implemented)
go run . -mode search

# Connection mode (to be implemented)
go run . -mode connect
📁 Project Structure
linkedin-automation/
├── main.go              # Entry point, configuration, CLI
├── automation.go        # Core automation logic
├── stealth.go          # Anti-detection techniques
├── go.mod              # Go module dependencies
├── go.sum              # Dependency checksums
├── .env.example        # Example configuration
├── .env                # Your configuration (gitignored)
├── user-data/          # Chrome user data directory
└── README.md           # This file
🔧 Configuration
Environment Variables
VariableDescriptionDefaultUSER_DATA_DIRChrome user data directory./user-dataHEADLESSRun in headless modefalseSCROLL_DELAYDelay between scrolls2sACTION_DELAYDelay between actions3sMAX_SCROLLSMaximum scroll iterations5VIEWPORT_WIDTHBrowser viewport width1920VIEWPORT_HEIGHTBrowser viewport height1080USER_AGENTCustom user agent stringChrome 120 UA
Command Line Flags

-profile <url>: LinkedIn profile URL to visit
-mode <mode>: Operation mode (profile/search/connect)
-headless: Run in headless mode

🛡️ Anti-Detection Features Explained
1. WebDriver Property Masking

Removes navigator.webdriver property
Deletes automation-related window properties
Overrides CDP runtime detection

2. Canvas Fingerprinting Protection

Adds subtle noise to canvas rendering
Makes fingerprints unique but realistic
Prevents tracking across sessions

3. Browser Fingerprint Randomization

Randomizes plugin enumeration
Varies screen properties
Modifies connection information

4. Timing Attack Prevention

Adds variance to Date.now() and performance.now()
Prevents detection through timing consistency
Mimics real user timing patterns

5. Audio & WebGL Masking

Adds noise to audio context analysis
Spoofs WebGL renderer information
Prevents hardware fingerprinting

🎭 Human Behavior Simulation
Natural Scrolling
go// Variable speed scrolling with easing
// Occasional scroll-backs (like re-reading)
// Random pauses between scrolls
Mouse Movement
go// Bezier curve-based movement
// Realistic acceleration/deceleration
// Random path variation
Typing Simulation
go// Variable typing speed (150-300ms per char)
// Occasional pauses (thinking)
// Realistic keystroke timing
Reading Time Calculation
go// Based on average reading speed (200-250 WPM)
// Adds realistic variance
// Adjusts for content length
🔐 Security Best Practices

Never commit credentials: Use environment variables only
Respect rate limits: Implement delays between actions
Use user data directory: Maintain persistent sessions
Monitor for CAPTCHAs: Detect and stop on CAPTCHA challenges
Rotate user agents: Don't use the same UA for all requests
Limit automation scope: Don't automate aggressively

📊 Performance Considerations

Memory Usage: Chrome instances consume 200-500MB RAM each
CPU Usage: Rendering and JS execution are CPU-intensive
Network: Respect LinkedIn's servers; add delays
Disk Space: User data directory grows over time

🧪 Testing
bash# Run with verbose logging
go run . -profile "..." -mode profile 2>&1 | tee automation.log

# Test stealth features
# Visit: https://bot.sannysoft.com/
# Should pass most detection tests

# Test fingerprint uniqueness
# Visit: https://abrahamjuliot.github.io/creepjs/
🛠️ Development
Adding New Automation Modes

Add mode to automation.go
Implement mode-specific logic
Update configuration if needed
Add tests and documentation

Example:
gofunc (la *LinkedInAutomation) performNewMode(ctx context.Context) error {
    log.Println("New mode implementation")
    // Your automation logic here
    return nil
}
Extending Stealth Features
Add new techniques to stealth.go:
gofunc (sm *StealthManager) GetAdvancedStealthScript() string {
    return `
        // Your new stealth JavaScript here
    `
}
📈 Roadmap

 Search automation implementation
 Connection request automation
 Message sending automation
 Advanced CAPTCHA detection
 Proxy rotation support
 Multi-account management
 Analytics and reporting
 Database integration for data storage
 API for external integrations
 Docker containerization

⚖️ Legal & Ethical Considerations
Important: This tool is for educational purposes only.

✅ Use for learning about browser automation
✅ Use for understanding anti-detection techniques
✅ Use for personal research projects
❌ Don't use for spam or harassment
❌ Don't violate LinkedIn's Terms of Service
❌ Don't use for unauthorized data collection
❌ Don't use for commercial purposes without permission

🐛 Troubleshooting
Chrome not found
bash# Install Chrome or set CHROME_PATH
export CHROME_PATH=/path/to/chrome
Login issues
bash# Run without headless first
go run . -profile "..." -mode profile
# Login manually in the browser window
# Subsequent runs will use saved session
Rate limiting
bash# Increase delays in .env
SCROLL_DELAY=5s
ACTION_DELAY=10s
Memory issues
bash# Close other applications
# Reduce MAX_SCROLLS
# Enable headless mode
🤝 Contributing
Contributions are welcome! Please:

Fork the repository
Create a feature branch
Make your changes
Add tests if applicable
Submit a pull request

📝 License
MIT License - See LICENSE file for details
🙏 Acknowledgments

chromedp - Excellent Chrome DevTools Protocol library
puppeteer-extra-plugin-stealth - Inspiration for stealth techniques
LinkedIn Research Community

📬 Contact
For questions, suggestions, or collaboration:

Open an issue on GitHub
Submit a pull request
Reach out via email (if provided)


Remember: With great automation power comes great responsibility. Use ethically and legally.
