---
layout: page
title: Book Review: Operations Anti-Patterns, DevOps Solutions
date: 2020-12-01 15:46
author: AdinErmie
comments: true
categories: []
---
<a href="/wp-content/uploads/2020/12/OperationsAntiPatternsDevOpsSolutions-BookCover.png"><img class="alignleft size-medium wp-image-33708" src="/wp-content/uploads/2020/12/OperationsAntiPatternsDevOpsSolutions-BookCover-239x300.png" alt="" width="239" height="300" /></a>Recently, I finished reading <a href="https://www.manning.com/books/operations-anti-patterns-devops-solutions" target="_blank" rel="noopener noreferrer">Operations Anti-Patterns, DevOps Solutions</a> by Jeffery D. Smith.

I have experience with DevOps, but I found this book very enlightening. I really liked how it related real-world Operations patterns (which we all encounter), and how you can work to change those (for the positive) to follow a DevOps process.

I particularly liked Chapter 5 ("<strong>Quality as a Condiment</strong>"), and Chapter 10 ("<strong>Information Hoarding: Only Brent Knows</strong>").

If you work for an organization that is striving to shift to a DevOps workflow, I recommend that you read this book.

I’ve decided to share my highlights from reading this specific publication, in case the points that I found of note/interest will be of some benefit to someone else. So, here are my highlights (by chapter). Note that not every chapter will have highlights (depending on the content and the main focus of my work).

If my highlights peak your interest, I recommend that you pick up a copy for yourself.
<h2>Chapter 1: The DevOps Ingredients</h2>
<ul>
 	<li>DevOps isn’t about tools, but about how teams work together. There’s definitely technology involved, but honestly the tools are less important than the people.</li>
 	<li>If you don’t have a culture where automated testing is valuable, the tool doesn’t provide value.</li>
 	<li>DevOps is about people first, then process, then tools.</li>
 	<li>You need the people on board and ready for change. Once the people are on board, they need to be involved and engaged with creating the process. Once a process is created, you now have the necessary input to pick the right tool!</li>
 	<li>You can’t choose a tool and then tell the people that they have to change all their processes. Our brains are wired to immediately be hostile to that type of approach. When tools are launched like that, the tool feels like it’s happening to them, not through them.</li>
 	<li>With the rise of virtual machines, software defined networking and API access for creating infrastructure, it is no surprise that software development skills are becoming increasingly important for systems administrators and in many companies is already a strict requirement.</li>
 	<li>If system administrators survived the transition from token ring to IPX/SPX, to TCP/IP, to IPV6, I’m sure learning Python is not an insurmountable task.</li>
 	<li>DevOps is structured around four pillars of attention and focus. Those pillars are Culture, Automation, Metrics and Sharing (CAMS) as it's called for short.
<ul>
 	<li>Culture is about changing the norms by which your teams operate.</li>
 	<li>Automation is about freeing human capital from the mundane. It’s about empowering people to do their jobs safely and autonomously.</li>
 	<li>Metrics are the way you tell if something is working or not. The absence of errors is not sufficient.</li>
 	<li>Sharing is this idea that knowledge wants to be free! Humans often learn best when they’re teaching something to someone else.</li>
</ul>
</li>
 	<li>Lean. The idea is that delivering smaller, more frequent software updates is a preferred approach and that sometimes a minimal product in the hands of a customer is better than waiting six months for a more fleshed out version.</li>
 	<li>Technology is easy, it’s people that are hard. As such, you’ll need to put just as much effort into solving your cultural issues as you will your technology ones.</li>
 	<li>Developing a system is useless if you can’t operate it effectively once it’s in production.</li>
 	<li>DevOps is more than just a new set of tools. DevOps is truly about redefining the way you look at work and the relationships between work.</li>
</ul>
<h2>Chapter 2: The Paternalist Syndrome</h2>
<ul>
 	<li>It’s about a lack of trust between each other and a lack of safety inside your systems.</li>
 	<li>When safety is missing in your systems it manifests in the form of hand-offs, approvals and overly restrictive access controls.</li>
 	<li>Instead of solving these issues through collaboration, organizations instead erect barriers between teams, filling the void with process, access restrictions and hand-offs.</li>
 	<li>In many organizations it’s not long before change approval is considered a hurdle rather than a value-add process.</li>
 	<li>DevOps focuses on maximizing the work you do that will bring lasting value to the organization.</li>
 	<li>The goal of DevOps is the following:
<ul>
 	<li>Increase collaboration among teams</li>
 	<li>Decrease unnecessary gates and handoffs</li>
 	<li>Empower development teams with the tools and authority to own their systems</li>
 	<li>Create repeatable, predictable processes</li>
 	<li>Share responsibilities for the application production environment</li>
</ul>
</li>
 	<li>Being able to confirm that something is working is more valuable than just being able to confirm there are no errors.</li>
 	<li>As the level of automation and the amount of shared responsibility increases, the incentives for information hoarding begin to crumble.</li>
 	<li>If the world can automate a jet-liner landing, I assure you that you’re up to the task of automating your approval process.</li>
 	<li>Structure even the most mundane of scripts with the thoughtfulness you would afford a full-blown application. Try to think about how the script has different concerns and try to separate those concerns into manageable, maintainable code.</li>
</ul>
<h2>Chapter 3: Operational Blindness</h2>
<ul>
 	<li>Understanding the product you’re supporting leads to a better understanding of the types of metrics that you need to generate and monitor to verify that your system is functioning as expected.</li>
 	<li>The first step in creating operational visibility is to go beyond the system metrics and develop custom metrics for your application.</li>
 	<li>Creating custom metrics is a must in order to bring greater operational visibility to your application.</li>
 	<li>Never settle for only the metrics you currently have. You should be continuously asking yourself questions about your system and ensuring that you can answer those questions through metrics.</li>
 	<li>Observability gives you the visualization capabilities of metrics along with the fine-grained, detailed information that you get from logging.</li>
 	<li>remember that a central tenant of DevOps is to empower teams and to share and democratize as much information as possible.</li>
 	<li>Getting the log message in the right category is almost as important as logging the message in the first place. Too many down stream actions like search, filtering and even monitoring depend on the categorization of the log message being correct.</li>
 	<li>You shouldn’t only log for troubleshooting purposes. You can think about logging for audit purposes as well as profiling purposes.</li>
</ul>
<h2>Chapter 4: Data Instead of Information</h2>
<ul>
 	<li>Data is just raw unorganized facts but when you take that data, give it context and structure it becomes information.</li>
 	<li>This is why starting with your user in mind is a dashboarding best practice. Understand the motivations for what the user will be doing.</li>
 	<li>You should think about the user and the key bits of information they will need when viewing this dashboard. Think of the big two to four items that you think will be the most likely reason your intended users are coming to the dashboard.</li>
 	<li>The first row of the dashboard should be reserved for your most important metrics. Where they fall in the grouping of metrics is immaterial compared to how quickly you can get access to that data.</li>
</ul>
<h2>Chapter 5: Quality as a Condiment</h2>
<ul>
 	<li>Waiting until the end of the development lifecycle and tacking on testing can be a recipe for disaster.</li>
 	<li>If properly designed, any unit test failure should result in tests higher in the stack failing pretty reliably.</li>
 	<li>Unit tests should be written by the developer writing the component or unit under test. The reason being that unit tests should be run regularly by the developer during the creation and subsequent testing of the unit under development!</li>
 	<li>Integration tests should never run their integration points against production instances.</li>
 	<li>Vanity metrics are things that you measure in your system that are easily manipulated and don’t provide a clear picture of the thing they proport to measure.</li>
 	<li>But in reality, test coverage is an example of a vanity metric. Coverage doesn’t necessarily speak to the quality of the test or what specifically is being tested.</li>
 	<li>Test coverage is great, but not having 100% test coverage doesn’t mean your testing suite isn’t extremely robust. And having 100% test coverage doesn’t mean your testing suite is doing anything worthwhile. You must look beyond the numbers and focus on the quality of those tests.</li>
 	<li>The main difference is that with continuous deployment, every change that gets committed to the main branch gets released through an automated process, with no manual intervention. With continuous delivery, the focus is more on ensuring the capability to deploy code when needed without having to wait for a large release train with a bunch of other changes. Every commit may not be released automatically, but it could be released at any time if needed.</li>
 	<li>You need rock solid automated testing if you’re going to deploy every commit to production. You need a solid code review process to ensure multiple sets of eyes have looked at code from whatever review criteria your teams have setup.</li>
 	<li>The takeaway is that the requirements that you have for releasing software can and should be codified as much as possible and placed into a pipeline of some sort.</li>
 	<li>Once you’ve chosen a tool, it’s important that you break your pipeline into separate distinct phases. This is so that you can give your developers rapid feedback on their pipeline execution and to assist in pinpointing where the process has broken down.</li>
 	<li>A DevSecOps approach requires the embedding of security scans and tests as part of the pipeline solution, very similar to the way testing should operate.</li>
 	<li>If you want a more expansive discussion, I recommend the book DevOpsSec by Jim Bird (<a href="https://www.amazon.com/DevOpsSEC-DELIVERING-SOFTWARE-CONTINUOUS-DELIVERY/dp/1491958995/ref=sr_1_1?dchild=1&amp;keywords=DevOpsSec+Jim+Bird&amp;qid=1591116621&amp;sr=8-1" target="_blank" rel="noopener noreferrer">https://www.amazon.com/DevOpsSEC-DELIVERING-SOFTWARE-CONTINUOUS-DELIVERY/dp/1491958995/ref=sr_1_1?dchild=1&amp;keywords=DevOpsSec+Jim+Bird&amp;qid=1591116621&amp;sr=8-1</a>) or Securing DevOPs by Julian Vehent (<a href="https://www.amazon.com/Securing-DevOps-Security-Julien-Vehent/dp/1617294136/ref=sr_1_1?dchild=1&amp;keywords=vehent+security&amp;qid=1591116268&amp;sr=8-1" target="_blank" rel="noopener noreferrer">https://www.amazon.com/Securing-DevOps-Security-Julien-Vehent/dp/1617294136/ref=sr_1_1?dchild=1&amp;keywords=vehent+security&amp;qid=1591116268&amp;sr=8-1</a>) as great resources.</li>
 	<li>Automated scanning utilities that are capable of not only scanning your code but also resolving the transitive dependencies in your codebase and scanning those libraries for vulnerabilities is a must.</li>
</ul>
<h2>Chapter 6: Alert Fatigue</h2>
<ul>
 	<li>Let’s talk about what makes a good alert. First, an alert should have some sort of associated documentation with it.</li>
 	<li>A good alert is
<ul>
 	<li>Actionable. When the alert triggers it points to the problem and a path for the solution. The solution should be defined in the alert message or in the runbook. Linking directly to the runbook inside of the alert notification eliminates the difficulty of finding the correct runbook for a given scenario.</li>
 	<li>Timely. The alert does as little forecasting on the impact as possible. When the alert fires, you feel confident that you need to investigate it immediately, versus waiting five minutes to see if the alert clears on its own.</li>
 	<li>Properly prioritized. It’s easy to forget that alerts do not always have to wake someone in the middle of the night. For alerts that are needed for awareness, convert those to lower-priority notification methods such as email.</li>
</ul>
</li>
 	<li>When you come across a useless alert, you need to put as much energy as possible into either fixing it to be more relevant or just completely deleting it.</li>
 	<li>When designing anomaly-based alerts be sure that you think about the various cycles that the metric your alerting on goes through and that there will be enough data for the algorithm to detect those patterns.</li>
 	<li>The minimum long-term size of an on-call rotation is four staff members.</li>
</ul>
<h2>Chapter 7: The Empty Toolbox</h2>
<ul>
 	<li>You must think beyond just the product or feature being built when it comes to tooling and automation. You must think of the entire system around the product.</li>
 	<li>A manual process, no matter how well documented, always offers the opportunity for failure. Humans are just not built for these repetitive tasks that computers excel at.</li>
 	<li>In so many scenarios our urgency to get a thing done prevents us from doing things the way they should be, with proper automation and tooling.</li>
 	<li>Automation is no longer optional. If you’re going to be successful, automation must become a priority in your project, your work and your tools.</li>
 	<li>Always keep in the back of your mind that when it comes to automation, the safety of execution is always something to design for.</li>
</ul>
<h2>Chapter 8: Off-Hour Deployments</h2>
<ul>
 	<li>One of the ways you make an activity routine is to do it in a controlled environment beforehand. The more you can make the environment like the real thing, the better and more comfortable you become.</li>
 	<li>making the staging environment mimic production as closely as possible in terms of architecture and topology. If there are multiple instances of an application service, on separate machines in production, the same pattern should be replicated in the staging environment.</li>
 	<li>Getting more automated testing into the pipeline is going to be the baseline for any sort of automated deployment pipeline.</li>
 	<li>Enforce the idea that merge requests without test cases are incomplete merge requests. Make it part of the code review process or even better, make it part of your build pipeline!</li>
 	<li>The blue/green deployment is of course the holy grail of public/private cloud infrastructure.</li>
 	<li>The primary rule for database changes is this. You always try to make additive changes to the database. Avoid changing things that are already in place, because somewhere there’s probably a dependency on it which will be impacted by your change. Instead, always try to move the database schema forward by making additions to the schema.</li>
 	<li>The key to database versioning is to know all of the SQL statements that were executed to get your database to the point that it’s currently at. Any engineer should be able to run a series of commands to bring the database to a specific version, where the table schema matches as expected.</li>
 	<li>If you want to move to a DevOps workflow, managing your servers via some form of configuration management is table stakes.</li>
</ul>
<h2>Chapter 9: Wasting a Perfectly Good Incident</h2>
<ul>
 	<li>The reason the blame game doesn’t work is because it attacks the people as the problem.</li>
 	<li>With a blameless culture, the attention shifts from everyone attempting to deflect blame, to solving the problems and gaps in knowledge that led to the incident.</li>
</ul>
<h2>Chapter 10: Information Hoarding: Only Brent Knows</h2>
<ul>
 	<li>How you share information is always going to be a blueprint for how you communicate as a team and how you draw the lines of responsibility and ownership.</li>
 	<li>Access restrictions start off with the best of intentions but if they’re not carefully monitored, they can quickly spiral into an over-protective police state.</li>
 	<li>Scientists and psychologists have identified four primary methods of learning that people adopt to; visual, auditory, reading/writing and kinesthetic or hands-on activities.</li>
 	<li>Starting with a clear topic is the first step of communication.</li>
 	<li>Once your topic is defined, you’ll want to think about who you plan to communicate this to. Understanding who you’re speaking to will help you choose the level of depth your topic must go into on some bits of knowledge.</li>
 	<li>Once you have the topic defined and your audience selected, structuring your key points is next.</li>
 	<li>Your key points are areas of the topic that you want to communicate. It can be separated into two camps, core and color.</li>
 	<li>Your core group are things that you are absolutely committed to communicating and are essential to understanding the topic. Color points are areas that help to enhance understanding but may not be vitally important to communicating the topic at hand.</li>
 	<li>Finally, at the end comes the call to action. What is the audience supposed to do with that information and what are those next steps?</li>
 	<li>Creating a common lexicon and naming strategy for business processes, services, systems and tools isn’t meant to help the 15-year veterans of the company. It’s designed to help the new hires in the organization get up to speed quickly on the inner workings of the company instead of trying to figure out if two things are in fact identical.</li>
 	<li>In many organizations, no where is there a complete document highlighting the entire process from start to finish. Instead each department splinters into their own</li>
 	<li>groups and writes documentation that addresses their specific area or focus on the process.</li>
 	<li>The master document should focus on a process, application or system and provide a jumping off point for any specific departmental information if necessary.</li>
 	<li>Documentation should form a hierarchical structure, leading back to the master document that it covers, and that master document should be concise and specific about a topic.</li>
 	<li>Another thing that is encouraged with the introduction of master documents is the idea that your documentation should be structured around topics instead of departments.</li>
</ul>
<h2>Chapter 11: Culture By Decree</h2>
<ul>
 	<li>Culture goes beyond the fun activities at office parties and the wide variety of gluten-free snacks provided in the break room.</li>
 	<li>Cultural values however do not exist in a vacuum. Values are just declarations without action. Cultural norms are the activities that bring cultural values into something tangible.</li>
 	<li>Cultural values without cultural norms are just empty platitudes.</li>
 	<li>When you interact with other teams you want to use language that does the following.
<ul>
 	<li>Explicitly separates hard fact from perspectives or opinions that are drawn from that fact.</li>
 	<li>Use phrasing that opens the room for debate</li>
 	<li>Establish the end-goal of your action.</li>
</ul>
</li>
 	<li>One of the biggest skills that engineers have (or should have) is the ability to learn!</li>
 	<li>The typical interview process is the most unnatural setting to assess someone’s skills for a job.</li>
</ul>
<h2>Chapter 12: Too Many Yardsticks</h2>
<ul>
 	<li>Knowing your goals and how they factor into the larger set of organizational goals is, for many people, an influencer of job satisfaction.</li>
 	<li>When your work is off on an island and nobody appreciates what you do or why you do it, you can become disconnected from the rest of the organization. As everyone marches on toward goals that get talked about in company-wide meetings, you’re on the sidelines wondering why you’re doing what you’re doing and if it matters at all.</li>
 	<li>Knowing that their work matters and is impactful to people outside the organization can be an enormous team motivator.</li>
 	<li>When it comes to individuals, commitments are the currency of credibility. When someone commits to something, you instantly do a calculation on that person’s credibility.</li>
 	<li><strong>Pro Tip:</strong> Refusing a task is more professional than accepting it and never doing it.</li>
 	<li><strong>Pro Tip:</strong> Unless you have complete control over how your work is prioritized, you never want to offer commitments that you may have no control over honoring. This is important not only for the requestor, but for your own personal reputation in the organization.</li>
 	<li>A to-do list with 50 items on it can instantly put you in a state of analysis paralysis, preventing you from making progress on anything.</li>
 	<li>In a two-week iteration my rule of thumb is no more than four work items per person.</li>
 	<li>It can take an engineer between 15 and 30 minutes to get back into the previous mental state before the unplanned work.</li>
</ul>
