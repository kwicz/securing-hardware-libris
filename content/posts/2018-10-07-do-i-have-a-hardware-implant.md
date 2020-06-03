---
layout: post
title: Do I Have a Hardware Implant?
featured: images/pic03.jpg
thumb_image: images/4.jpg
image: images/3.jpg
author: joefitz
---

I've gotten lots of inquiries from people who want to know if I could analyze some hardware for them or could recommend someone who might. I'll be blunt - most of you don't need this. Here are some things you should consider before seeking out services like this:

1. It's unlikely you're affected. Really. Even assuming every claim is true, and even if there is a secret device on every single X brand motherboard, it's unlikely you're targeted by whatever payload the implant carries.

2. There are no published indicators of compromise (IOCs). The device and placement referenced in the article are only representative and not actual devices. Having experienced hardware eyes on your board might pick out something odd, but won't be conclusive.

3. Without an IOC, you need to do a time consuming, thorough, invasive, destructive analysis of every component on your board. This is EXPENSIVE. If it's not time consuming, invasive, destructive, and expensive, you're not getting a thorough job.

4. If you're sure you're ready to drop 6, maybe 7 figures to get this job done right, are you sure you've covered all your other bases? Experts all ask why an attacker would do a hardware attack when there are so many easier software/firmware vectors. Is your budget better spent there?

5. Beware of ambulance chasers. There really are only a handful of people and companies equipped to offer these kind of services or with relationships to subcontract them. You want someone who's done this kind of job many times before. 

6. Again. There are no IOCs yet. Spend your money planning your response for when (not if) there are. Spend your money planning for hardware security acceptance criteria for your next hardware refresh.

Let's say you actually do run something that really is critical infrastructure. You've already got a well established and properly funded security program. You've already got a culture of security where vulnerabilities are taken seriously and fixed.

If all of the above is true, then you've probably considered hardware attacks in your threat model, & might benefit from taking a closer look, but make sure you know what you're paying for. If this is your first time getting a hardware assessment, prepare for sticker shock.

No matter what, hardware attacks belong in your threat model, but until all of the above is true, an assessment specifically looking for hardware implants on production equipment is a misallocation of attention and money is better spent elsewhere.


What would a thorough assessment include?
=========================================
This is not a small job. This is not a cheap job. Expect a server motherboard to have at least 10^1 components with firmware, 10^2 active logic components, and 10^3 passive components. Every one needs analysis.

1. Take a complete inventory of every component. This should be compared against the most detailed documentation you can get from your board vendor. This is where the leverage of being a volume customer is valuable.

2. If there are any unexpected modules, add-ons, or blue/bodge/repair wires, confirm they're supposed to be there with the vendor. If not, exhaustively analyse them first.

3. Next, if there are any extra parts, identify them by their markings. Electrically analyze their inputs and outputs in a live system. Remove the part. Dump and analyze any firmware it might have. Decap and image the part. Compare to a known good identical part.

4. Next, X-ray the whole board. Identify any differences between your board and board layout diagrams. Identify any components that don't look exactly like they should, and repeat the component analysis process on each of them

5. Repeat component analysis on every other component. Prioritize components on low speed serial busses, followed by components that are unmarked, followed by larger and active components

6. Continue all the way down to passive components. These might be doable in batches. You might think you can skip this step, but if you actually want a thorough assessment, this is not negotiable.


I Found Something!
==================

Take off your tinfoil hat. If something is different, rule out an engineering or business reason before assuming malicious intent. Sometimes docs are outdated, chips are interchangable, board errors are fixed, and market prices for compatible replacements shift.

Next, rule out simple profit motives. Bunnie has an excellent coverage of the range of counterfeit devices. Pretty much every picture you've ever seen of a hardware implant is really a counterfeit bypass device. <a href="https://www.bunniestudios.com/blog/?p=2037">https://www.bunniestudios.com/blog/?p=2037</a>

If you've gotten this far, you're on to something. If you're bold, you could be the first to publicly disclose full details of an actual malicious hardware implant. Double up on your foil, find a bunker, use tor, use signal, and tell everyone.

Yes I'm Serious
===============
My commentary might be sarcastic, but with good reason. Hardware implants are real and techincally possible. We see modchips, counterfeit bypass devices, keystroke loggers, and card skimmers all the time - but we've never actually seen deployed hardware backdoors in servers.

<a href="https://twitter.com/syncsrc">@syncsrc</a> said it to me best: TL,DR - if you haven't talked to your vendors about the supply-chain integrity mechanisms they have in place, tearing down a few motherboards for analysis won't solve your problems.
