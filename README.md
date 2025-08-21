<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Scalable Operating System</title>
    <style>
        /* General Reset & Responsive Foundation */
        @import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700;800&display=swap');

        html, body {
            margin: 0;
            padding: 0;
            font-family: 'Inter', sans-serif;
            background-color: #0b0c10; /* Dark, subtle background */
            color: #f9f9f9; /* Light text for contrast */
            line-height: 1.6;
            overflow-x: hidden;
            scroll-behavior: smooth;
        }

        /* Main Container for Content */
        .container {
            width: 100%;
            max-width: 1000px;
            margin: 0 auto;
            padding: 20px;
            box-sizing: border-box;
        }

        /* Sections with Fade-in Animation */
        .fade-in-section {
            opacity: 0;
            transform: translateY(20px);
            transition: opacity 0.6s ease-out, transform 0.6s ease-out;
            will-change: opacity, transform;
            margin-bottom: 5rem;
        }
        .fade-in-section.is-visible {
            opacity: 1;
            transform: translateY(0);
        }

        /* Responsive Text and Spacing */
        h1, h2, h3, h4, h5, h6 {
            font-family: 'Inter', sans-serif;
            font-weight: 800;
            line-height: 1.1;
            margin-top: 2rem;
            margin-bottom: 1rem;
        }

        h1 { font-size: clamp(2.5rem, 6vw, 4.5rem); text-transform: uppercase; }
        h2 { font-size: clamp(2rem, 5vw, 3.5rem); }
        h3 { font-size: clamp(1.75rem, 4vw, 2.5rem); }
        p { font-size: clamp(1rem, 2vw, 1.2rem); margin-bottom: 1.5rem; color: #b1b1b1; }

        @media (max-width: 768px) {
            .container { padding: 15px; }
            h1 { font-size: 2.2em; }
            h2 { font-size: 1.8em; }
            h3 { font-size: 1.5em; }
            p { font-size: 1em; }
        }

        /* Visual & Layout Styles */
        .text-center { text-align: center; }
        .hero-section {
            padding-top: 8vh;
            text-align: center;
        }
        .hero-section p { max-width: 800px; margin: 0 auto 2rem auto; }

        /* CTA Button */
        .cta-button {
            display: inline-block;
            background: linear-gradient(45deg, #1e90ff, #0056b3);
            color: white;
            padding: 1.2em 3em;
            border-radius: 50px;
            text-decoration: none;
            font-size: 1.1em;
            font-weight: 700;
            letter-spacing: 1px;
            transition: transform 0.2s ease, box-shadow 0.2s ease;
            box-shadow: 0 5px 20px rgba(30, 144, 255, 0.3);
            border: none;
            cursor: pointer;
            margin: 2.5rem 0;
        }
        .cta-button:hover {
            transform: translateY(-5px);
            box-shadow: 0 8px 30px rgba(30, 144, 255, 0.5);
        }

        /* VSL Icon Styling */
        .vsl-icon {
            position: relative;
            width: 100%;
            max-width: 700px;
            height: 0;
            padding-bottom: 56.25%; /* 16:9 aspect ratio */
            background-color: #2c2f33;
            border-radius: 15px;
            overflow: hidden;
            margin: 2rem auto;
            cursor: pointer;
            box-shadow: 0 10px 30px rgba(0,0,0,0.3);
        }
        .vsl-icon::before {
            content: '';
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            width: 80px;
            height: 80px;
            background: rgba(255, 255, 255, 0.1);
            border: 2px solid rgba(255, 255, 255, 0.2);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            z-index: 10;
        }
        .vsl-icon::after {
            content: '▶';
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            font-size: 3rem;
            color: #1e90ff;
            z-index: 11;
        }

        /* Visual Separator */
        .divider {
            border: none;
            height: 2px;
            background: linear-gradient(90deg, transparent, #2c2f33, transparent);
            margin: 6rem auto;
            max-width: 80%;
        }

        /* Bullet Points */
        .bullet-list {
            list-style: none;
            padding: 0;
            margin: 2rem 0;
        }
        .bullet-list li {
            position: relative;
            padding-left: 2em;
            margin-bottom: 2em;
            font-size: 1.1em;
            font-weight: 500;
            color: #b1b1b1;
        }
        .bullet-list li strong { color: #f9f9f9; }
        .bullet-list li:before {
            content: '✔';
            position: absolute;
            left: 0;
            color: #1e90ff;
            font-weight: bold;
        }

        /* Testimonial Section */
        .testimonial-container {
            margin-top: 3rem;
            margin-bottom: 3rem;
        }
        .testimonial {
            background-color: #1c1e26;
            padding: 2.5rem;
            border-radius: 10px;
            box-shadow: 0 5px 15px rgba(0,0,0,0.2);
            font-style: italic;
            border-left: 5px solid #1e90ff;
        }
        .testimonial p { color: #b1b1b1; font-style: italic; }

        /* Utility classes for emphasis */
        .preheader {
            font-size: clamp(1rem, 2vw, 1.2rem);
            font-weight: 500;
            color: #8c8c8c;
            margin-bottom: 0.5rem;
        }
        .subheader {
            font-size: clamp(1.2rem, 3vw, 1.8rem);
            font-weight: 400;
            color: #8c8c8c;
            margin-top: 0.5rem;
        }
        strong { font-weight: 700; color: #f9f9f9; }
        em { font-style: italic; color: #1e90ff; }
        .caps { text-transform: uppercase; letter-spacing: 1px; }

    </style>
</head>
<body>
    <div class="container">
        <!-- HERO SECTION -->
        <div class="hero-section fade-in-section">
            <p class="preheader">
                To the founder feeling trapped by their own success...
            </p>
            <h1>
                Install a System That Runs Your Business... <br>
                <em>While You Step Away.</em>
            </h1>
            <p class="subheader">
                Finally build a company that runs itself... without you getting stuck in endless meetings, micromanaging your team, or doing all the firefighting yourself.
            </p>
            <div class="vsl-icon" onclick="alert('Video playing... just kidding, it's a demo! :)');"></div>
            <a href="#cta" class="cta-button">
                Secure Your Freedom Call
            </a>
        </div>
        <hr class="divider">

        <!-- PROBLEM IDENTIFICATION -->
        <div class="section-problem fade-in-section">
            <h2>The Silent Killer of High-Growth Businesses.</h2>
            <p>
                You’ve done it. You built the thing. You grew the company to millions in revenue.
            </p>
            <p>
                But it’s not what you imagined.
            </p>
            <p>
                You’re a highly paid firefighter... an over-caffeinated bottleneck... the person every single team member turns to when something goes wrong.
            </p>
            <p>
                The business owns you, not the other way around.
            </p>
            <p>
                You’ve bought the time management planners. Hired the “integrators” who just needed more of your time to integrate. You’ve even tried to create a million SOPs that nobody ever uses.
            </p>
            <p>
                And the frustration grows.
            </p>
            <p>
                Because you can see the future... the stress eating away at your health... the missed soccer games and late dinners... the feeling that your life is just one big meeting after another.
            </p>
            <p>
                What’s the real cost of this?
            </p>
            <p>
                It’s not just the missed time. It’s the constant low-level dread. The feeling that everything is just one bad hire away from falling apart. The knowledge that if you took a real vacation, the entire operation would grind to a halt.
            </p>
            <p>
                But what if there was another way? A way that wasn't about more effort, but about a better structure.
            </p>
        </div>
        <hr class="divider">

        <!-- ORIGIN STORY -->
        <div class="section-origin fade-in-section">
            <h2>The Moment I Realized We Were Doing It All Wrong.</h2>
            <p>
                For years, I believed the lie that more success meant more work.
            </p>
            <p>
                My own business grew... but I became the chief problem-solver, the central point of failure. I was taking calls at all hours, feeling the weight of every decision. My freedom was gone. My family started to notice.
            </p>
            <p>
                I knew there had to be an escape hatch.
            </p>
            <p>
                So I started to map out every single process. Not just in a document, but visually... on a whiteboard... seeing how everything connected.
            </p>
            <p>
                The breakthrough happened when I realized it wasn't about documenting every tiny detail. It was about identifying the critical levers. The 20% of actions that produced 80% of the results.
            </p>
            <p>
                The conventional advice tells you to work harder. To hire more people. To use more tools. All of that just builds a bigger, more complex cage.
            </p>
            <p>
                What I found was the exact opposite. By focusing on the right few systems, the chaos disappeared. My team became self-sufficient. I finally felt a deep calm.
            </p>
            <p>
                That’s what led to this.
            </p>
        </div>
        <hr class="divider">

        <!-- SOLUTION REVELATION -->
        <div class="section-solution fade-in-section">
            <h2>This Is How Your Business Runs Without You.</h2>
            <p>
                It’s called the **Scalable Operating System (SOS).**
            </p>
            <p>
                Think of it like building the nervous system for your business. It's not a spreadsheet or a software... it's a living framework that takes the best of what you do and puts it into a repeatable, scalable engine.
            </p>
            <p>
                We start by visually mapping out your value drivers... the handful of processes that actually make you money.
            </p>
            <p>
                From there, we build out the critical playbooks... the cheat sheets your team can use to make decisions without asking you.
            </p>
            <p>
                And then we connect it all to a central operating dashboard... a single screen that shows you exactly what’s happening in your company at any given moment.
            </p>
            <p>
                <strong>Before:</strong> You're on your tenth call of the day, someone's asking you to approve a minor expense, and you're mentally running through your to-do list for the next week. You feel like you're drowning.
            </p>
            <p>
                <strong>After:</strong> You’re getting a summary email while on a hike. You open your phone, glance at the company scorecard, see all the KPIs are green, and close the email without a single thought about work. You feel a deep peace of mind.
            </p>
            <p>
                Because the system is running the business.
            </p>
            <ul class="bullet-list">
                <li>
                    <strong>Critical Playbooks</strong> for every key function ➡ so your team has a source of truth ➡ making you the owner, not the operator.
                </li>
                <li>
                    <strong>Company Scorecards & KPIs</strong> ➡ so you get real-time data on performance ➡ giving you confidence in your team and your company's health.
                </li>
                <li>
                    A <strong>Centralized Operating Dashboard</strong> ➡ so you have total visibility from a single screen ➡ making you the calm, strategic CEO you were meant to be.
                </li>
            </ul>
        </div>
        <hr class="divider">

        <!-- PRODUCT INTRODUCTION -->
        <div class="section-product fade-in-section">
            <h2>Introducing the Scalable Operating System Implementation.</h2>
            <p>
                This isn't just another program. It’s a <strong>12-16 week, one-on-one process</strong> where we work directly with you and your team to install this system.
            </p>
            <p>
                Remember all those systems and projects that sit on your shelf collecting dust? This isn't one of them.
            </p>
            <p>
                While other solutions give you a manual and a pat on the back, we sit beside you in the weeds, getting the work done.
            </p>
            <ul class="bullet-list">
                <li>
                    <strong>Step 1: Systemize Execution.</strong> We map out your value drivers and create the playbooks that get you out of the day-to-day firefighting.
                </li>
                <li>
                    <strong>Step 2: Optimize Operations.</strong> We install your company scorecards and meeting rhythms to create a culture of ownership and accountability.
                </li>
                <li>
                    <strong>Step 3: Scale With Clarity.</strong> We connect it all to your dashboard, giving you a clear view and a sellable company structure.
                </li>
            </ul>
            <p>
                The real question isn't what this costs... but what does it cost to keep doing what you're doing right now? The missed family time. The constant stress. The burnout waiting around the corner.
            </p>
        </div>
        <hr class="divider">

        <!-- OFFER STRUCTURE -->
        <div class="section-offer fade-in-section">
            <h2>Your Path to a Business That Thrives Without You.</h2>
            <p>
                This isn't for everyone. We only work with founders who are ready to let go and build something lasting.
            </p>
            <p>
                Your investment is significant... but the return is your life back.
            </p>
            <p>
                This isn't a program. This is a blueprint. We have a simple promise:
            </p>
            <p>
                <strong class="text-center"><em>"We work with you to install a Scalable Operating System that makes your business profitable, scalable, and capable of running without you."</em></strong>
            </p>
            <p>
                We can only work with a few new clients at a time to ensure we provide a truly hands-on, high-touch experience. Our availability is limited each quarter.
            </p>
        </div>
        <div class="cta-section fade-in-section" id="cta">
            <a href="https://your-calendar-link.com" class="cta-button">
                Book Your Strategy Call Now
            </a>
            <p>
                This call is not a hard sell. It’s a conversation to see if the Scalable Operating System is the right fit for your business and your goals.
            </p>
        </div>
        <hr class="divider">

        <!-- FAQ SECTION -->
        <div class="section-faq fade-in-section">
            <h2>Still Have Questions? Good.</h2>
            <div class="faq-item">
                <h4>Isn't this too expensive for me right now?</h4>
                <p>
                    What's the real cost of your time? The cost of having a business that can't grow without you? This isn’t a cost... it’s an investment in your freedom and the long-term value of your company.
                </p>
            </div>
            <div class="faq-item">
                <h4>What if this doesn't work for my specific business?</h4>
                <p>
                    The framework is a proven system, but the implementation is bespoke. It's built for your specific business... with your unique goals and your team. The system is designed to adapt, not to be a rigid one-size-fits-all solution.
                </p>
            </div>
            <div class="faq-item">
                <h4>I don’t think my team will adopt a new system.</h4>
                <p>
                    We know that’s the biggest barrier. That’s why we focus on team buy-in from day one. Instead of simply telling them what to do, we guide them in creating the systems themselves, which naturally increases adoption and ownership.
                </p>
            </div>
            <div class="faq-item">
                <h4>I'm worried about the time commitment.</h4>
                <p>
                    The truth is, you're already spending a huge amount of time on the wrong things. This 12-16 week process is a short, focused effort to eliminate the endless firefighting and create the space you need. You can't get your time back without investing some upfront.
                </p>
            </div>
        </div>
        <div class="cta-section fade-in-section">
            <a href="https://your-calendar-link.com" class="cta-button">
                Ready to Build Your Escape Hatch?
                <br>
                Book Your Call Now.
            </a>
        </div>
    </div>

    <script>
        // JavaScript for scroll-based fade-in animations
        const sections = document.querySelectorAll('.fade-in-section');

        const observerOptions = {
            root: null,
            rootMargin: '0px',
            threshold: 0.2
        };

        const observer = new IntersectionObserver((entries, observer) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    entry.target.classList.add('is-visible');
                    observer.unobserve(entry.target);
                }
            });
        }, observerOptions);

        sections.forEach(section => {
            observer.observe(section);
        });
    </script>
</body>
</html>
