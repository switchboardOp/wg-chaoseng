# Chaos Engineering

Although a wealth of variations exist the definitions of chaos engineering, we'll start with the one from the Principles of Chaos Engineering:

Chaos Engineering is the discipline of experimenting on a distributed system in order to build confidence in the system’s capability to withstand turbulent conditions in production.

Said otherwise:

Bad things will happen to your system, no matter how well designed it is. You
cannot become ignorant to it.

The definition covers most of the main important aspects of chaos engineering:

it is a discipline rather than a process. In other words, it leans on the actors capacity to stick to principles and making the right judgment call rather than having to follow prescriptive rules about how they must conduct their effort. The discipline usually emerges from the actors, and their unique needs
while this definition is specific about distributed system, where it provides the great benefits, chaos engineering is concerned about any system with enough complexity. It gives the actors a way of navigating this  complexity to learn and improve production is the main target of the effort. While actors could, and likely should, carry chaos engineering effort in their non-production environment, it is best performing it in production where it matters.

All of these facets are meant for actors to build confidence in their production
system and feel they can become familiar, and responsive, with its dynamic
nature.

Characteristics

The Principles of Chaos Engineering describe well the various characteristics of the discipline.

Vocabulary

Throughout this proposal, we will be using some terms that are fairly specific to the chaos engineering discipline:

hypothesis: question actors ask themselves about an aspect of their system's behavior after condition variations, described in terms of a result expressed as a quantity (ie. measurement)
experiment: investigation of the hypothesis through variable measurement and observability of the system's state 
instrument(ation): associate a particular result with an change in the system’s condition (the method of measurement)
calibration: identify and refine the amount of uncertainty included in a result.
observability: is a measure of how well internal states of a system can be inferred from knowledge of its external outputs. [https://en.wikipedia.org/wiki/Observability]  
Use Cases

So, what are the use cases for chaos engineering? As stated in the overview, there is no single golden rule applied across the board.

However, here are a few areas where it makes sense to carry chaos engineering
efforts:

Dependency on third-party providers out of actor's control: what is the effect of using provider X, when that provider goes down?
Network dependant services: Network cannot be trusted, even internal networking, can we cope with a link failure?
Service release impact may not be tested for peripheral aspects of the system: New release is made of one of the internal services, while its performances do not impact user's responsiveness, we note an increase in our costs due to poor resource management
Testing the engagement process and ensuring employees understand how to respond to pages and where playbook resources are: in other words, actors should hope to find answers, using chaos engineering experiments, regarding unhappy paths, especially cascading failure modes.
Surfacing unknown/transitive dependencies within a system: as systems become more complex the dependency graph and how stresses in one part of the system can cause other parts to change can become impossible to know holistically ahead of time.

Chaos Engineering in Cloud Native Systems

While chaos engineering is by no means focusing on a specific system architecture, it can have deep impacts on cloud native systems usage. Characteristics of cloud native systems that are interesting to chaos engineering:

dynamic: resources and services come and go and cannot be trusted to remain for any specific amount of time
promote isolation of concerns: outcomes of a well-focused chaos experiment should be easier to make sense of
automation: being API driven makes them great candidate for experimental automation needs
value observability: cloud native systems expose mechanisms for an operator to observe the live system's behavior, which is an inherent expectation of a well-crafted chaos experiment

In other words, cloud native systems characteristics lend themselves naturally
to chaos engineering and vice versa.

But, what's in it for cloud native users and operators? Would they conduct chaos experiments for the sake of it?

Cloud native systems abstract large chunks of complexity away from them. But it does not seem reasonable to assume this complexity disappears altogether. It is merely made simpler to deal with. Operators, and developers alike, must keep a level of familiarity and understanding of the stack they rely on in order to offer relevant responses in face of adversarial conditions.

In a nutshell, chaos engineering reminds the actors that the underlying system, for all its benefits, cannot be trusted nor become a black box.

Actors must remain active, and even proactive, in the lifecycle of their system.

WG Goals and Objectives

Creating a WG on chaos engineering has great value to capture the definition
and benefits the discipline could have on cloud native users. Indeed, while
the CNCF has done a great work to collate and structure the foundation of
cloud native, it feels the right time to help users learn how to fully make the
best of platforms and tooling they have at hand.

Chaos engineering is one practice, among others, that should be considered a
valuable asset.

However, much work remains to be done. While the folks at Netflix have done
an awesome job setting the grounds for the discipline (see the Principles of Chaos Engineering and the Chaos Engineering minibook), a CNCF WG could take this a step further
by helping an unified API for vendors to provide solutions to various aspects
of performing that discipline in a Cloud Native environment.

Questions that should be tackled by the WG:

1. What could be the scope of chaos engineering definition proposed under the
  CNCF umbrella?
  Is chaos engineering only about "breaking stuff"? Are there other approaches
  on learning about your system?
  Different actors, different perspective, different needs. Can we reconcile
  those into a unified package for all to benefit from?

2. What entrypoints should the WG define for chaos experiments?
  Right now, existing tools tend to frame: nodes, containers and networking.
  However, this is often done at a very low-level without any clear open API.
  Chaos experiments can be performed via well established API
  (say remove a Kubernetes service, preventing resolution of a given
  microservice). This leads to the next question.

3. Can the WG define a chaos engineering API so to speak?
  It seems like such an API, much like for networking and storage, will ensure
  diversity of vendors while reducing lock-in for users. Such an API could
  clarify aspects such as control vs data plane experiments, and provide
  entrypoints for both. The API means we should reach out to
  players across the board to consider the right entry points and measure
  their actual impacts.

4. How to extend observability API to support chaos experiments analysis?
  Chaos experiments without good observability makes readability of results
  much harder. Should the WG reach out to the observability players to see how
  they could also provide entry points for probes to collect information
  as a chaos experiment takes place?

5. How should the WG continue educating on this topic, define a landscape?
  While chaos engineering may seem trendy, it is far from being a natural
  given like other practices may be. It is necessary for the WG to accept that
  educating on this topic is an important goal. In particular, it is important
  to be clear that experimenting (trial) is not testing (in the traditional
  software meaning of the term).

6. Is there a potential CNCF project for chaos engineering?
  It seems right now, the best effort should be spent on givings responses to
  the above questions so that vendors can start providing implementations.
  Once that's done, the CNCF could start reviewing potential projects.

Non-Goals

A single project to handle chaos engineering needs

Governance
We expect to operate by rough consensus, however, if there’s an issue that cannot be resolved through rough consensus, we employ "organization voting" to ensure no single organization can dominate the project. Individuals not associated with or employed by a company or organization are allowed one organization vote. Each company or organization (regardless of the number of maintainers [https://github.com/chaoseng/wg-chaoseng/blob/master/MAINTAINERS] associated with or employed by that company/organization) receives one organization vote.
Resources

Principles of Chaos  (Netflix)  http://principlesofchaos.org/ 
Chaos Engineering (the book)  (Netflix) http://www.oreilly.com/webops-perf/free/chaos-engineering.csp
Chaos Engineering Upgraded (Netflix) https://medium.com/netflix-techblog/chaos-engineering-upgraded-878d341f15fa
ChAP: Chaos Automation Platform (Netflix) https://medium.com/netflix-techblog/chap-chaos-automation-platform-53e6d528371f
“AWS re:Invent 2017: Performing Chaos at Netflix Scale” https://www.youtube.com/watch?v=LaKGx0dAUlo
Chaos Community Google Group  (Netflix)  https://groups.google.com/forum/#!forum/chaos-community
Chaos Engineering Hands-On Bootcamp with K8s (Tammy Butow): https://github.com/tammybutow/chaos_engineering_bootcamp 
Chaos Engineering: history, principles and practice (Gremlin) https://www.gremlin.com/community/tutorials/chaos-engineering-the-history-principles-and-practice/
Gremlin Chaos Community  (Gremlin)  https://www.gremlin.com/community/
Chaos Conf  (Gremlin)  chaosconf.io 
Chaos Engineering Slack  (Gremlin)  gremlin.com/slack
Planning Your Own Chaos Day  (Gremlin)  https://www.gremlin.com/community/tutorials/planning-your-own-chaos-day/
Automating a Chaos Engineering Environment on AWS with Terraform  (Gremlin) https://www.gremlin.com/community/tutorials/automating-a-chaos-engineering-environment-on-aws-with-terraform/
Automating Failure Testing Research At Internet Scale (Netflix, Gremlin and UC Santa Cruz) https://people.ucsc.edu/~palvaro/socc16.pdf
The Evolution of Chaos Engineering (Gremlin) https://www.youtube.com/watch?v=hRwfLEc-0p4
Chaos Architecture talks and videos by Adrian Cockcroft (AWS)
    https://www.infoq.com/news/2017/11/cockcroft-chaos-architecture
    https://www.infoq.com/presentations/chaos-architecture-mindset 
A curated list of Chaos Engineering resources:
https://github.com/dastergon/awesome-chaos-engineering 
Landscape

Kubernetes-native chaos engineering
https://github.com/bloomberg/powerfulseal
https://github.com/jnewland/kubernetes-pod-chaos-monkey
https://github.com/asobti/kube-monkey
https://github.com/linki/chaoskube
The Simian Army - A suite of tools for keeping your cloud operating in top form.
Chaos Monkey - Version 2 of Chaos Monkey by Netflix
kube-monkey - An implementation of Netflix's Chaos Monkey for Kubernetes clusters.
Gremlin - Chaos-as-a-Service - Gremlin is a platform that offers everything you need to do Chaos Engineering. Supports all cloud infrastructure providers, Kubernetes, Docker and host-level chaos engineering. Offers an API and control plane. 
Pumba - Chaos testing and network emulation for Docker containers (and clusters).
Chaos Toolkit - A chaos engineering toolkit to help you build confidence in your software system.
ChaoSlingr - Introducing Security Chaos Engineering. ChaoSlingr focuses primarily on the experimentation on AWS Infrastructure to proactively instrument system security failure through experimentation.
drax - DC/OS Resilience Automated Xenodiagnosis tool. It helps to test DC/OS deployments by applying a Chaos Monkey-inspired, proactive and invasive testing approach.
Wiremock - API mocking (Service Virtualization) which enables modeling real world faults and delays
MockLab - API mocking (Service Virtualization) as a service which enables modeling real world faults and delays.
Pod-Reaper - A rules based pod killing container. Pod-Reaper was designed to kill pods that meet specific conditions that can be used for Chaos testing in Kubernetes.
Muxy - A chaos testing tool for simulating a real-world distributed system failures.
Toxiproxy - A TCP proxy to simulate network and system conditions for chaos and resiliency testing.
Blockade - Docker-based utility for testing network failures and partitions in distributed applications.
chaos-lambda - Randomly terminate ASG instances during business hours.
Namazu - Programmable fuzzy scheduler for testing distributed systems.
Litmus -  An open source framework for chaos engine based qualification of Kubernetes environments
https://github.com/guardicore/monkey: The Infection Monkey is an open source security tool for testing a data center's resiliency to perimeter breaches and internal server infection. The Monkey uses various methods to self propagate across a data center and reports success to a centralized Monkey Island server.

Interested Parties
Chris Aniszczyk (CNCF)
Toby Burress (Google)
Tammy Butow (Gremlin)
Matthew Fornaciari (Gremlin)
Sylvain Hellegouarch (ChaosIQ)
Michael Kehoe (LinkedIn)
Casey Rosenthal (Backplane.io)
Bruce Wong (StitchFix)
James Burns (Stitch Fix)
Alexei Ledenev (AWSCodefresh)
Aaron Rinehart (UHG)
Charles Torre (Microsoft)
Charles Nwatu (Stitch Fix)
Arun Gupta (AWS)
Adrian Cockcroft (AWS)
Ali Basiri (Netflix)
Sohan Kunkerkar (Red Hat)
Blaise Pabon (unaffiliated 5/2018)
Patrick Auld (PlanGrid)
Matt Jacobs (Gremlin)
Lorin Hochstein (Netflix) 
Kiran Mova (OpenEBS)
Ramin Keene (Fuzzbox)
Ho Ming Li (Gremlin)
Jason Hand (VictorOps)
Nora Jones (Netflix)
Karthik S (OpenEBS)
Adrian Hornsby (AWS)
Dan Dinu (Keysight)
Kris Raney (Keysight)
Winston Liu (Keysight)
João Rosa (Xebia (from 1st of June))
Mikolaj Pawlikowski (Bloomberg)
Matthew Brahms
Uma Mukkara (OpenEBS)
Sandeep Shilawat (ManTech)
Reda Benzair (Streamroot.io)
Brian Hammons (AWS)
Amit Kumar Das (OpenEBS)
Ahmed Hosni (Vistaprint)
Pavlos Ratis
Paul Jones (Capgemini UK)
Julien Bisconti (Discovery Networks Sweden)
Zack Hsi (Lyft)
Long Zhang (KTH Royal Institute of Technology)
Sean Keery (Pivotal)
