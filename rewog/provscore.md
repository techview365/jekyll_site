---
title: ProvsCore
description: 
layout: provscore
---
In general, Gnoppix Core is already very good for Linux beginners. The Gnoppix Core desktop has over 10,000 hours of development, which is my personal contribution to our society. Fortunately, Gnoppix has received backup from powerful companies, which will help to continue the Gnoppix story.

Exclusively to Gnoppix, we offer excellent hardware detection and premium Linux support. If you're new to Linux, you might feel intimidated to use it. Thankfully, with one of the best Linux distros for beginners, you don't have to possess any coding or programming experience.

--------------------------------------------------------------------------------------------------

| Feature                                                                       | PRO | Core | Devel
| ----------- | ----------- | ----------- | ----------- |
| [LTS version until 06/2028](https://docs.gnoppix.com/gnoppix-lts)             |  X  |   X  |  X
| Gnoppix IPTV                                                                  |  X  |      |
| Gnoppix run Windows app and games wizard                                      |  X  |      |  X
| Gnoppix Connect                                                               |  X  |      |  X
| Gnoppix Advantage Productivity                                                |  X  |      |  X
| Very Latest Software Versions, ex. Kernel, Windowmanger                       |  X  |      |  X
| Massive system and kernel changes                                             |  X  |   X  |  X
| Support for older hardware, i386                                              |  X  |   X  |  X
| Support for the development of Gnoppix                                        |  X  |      |
| Protection of your online fingerprint and user tracking                       |  X  |   X  |  X
| CEIV and HSCSC compliant Linux environment                                    |  X  |      |
| Bundeled Installation Support                                                 |  X  |      |
| Community Support                                                             |     |   X  |  X
| Security patches for common vulnerabilities and exposures socalled CVEs       |  X  |      |  X
| Dedicated infrastructure for ultrafast updates and downloads. 1GB/sec.        |  X  |      |  X
| Lightwighted, need less resouces                                              |  X  |      |  X

--------------------------------------------------------------------------------------------------


## When we started developing Gnoppix over 20 years ago

We had a vision: to prove that the power of Linux could be accessible to everyone, and that you didn't need to sacrifice your privacy or freedom to have a great and user-friendly computing experience.

Ever since, our team has worked tirelessly to turn this vision into a reality. We've designed Gnoppix to be a simple yet powerful Linux desktop that's easy to use for everyone, regardless of their technical expertise.

None of this could have been possible without the support of our community. We're grateful for the feedback, contributions, and encouragement we've received over the years.


## Gnoppix: A free and open-source Linux distribution that puts the user first

At Gnoppix, we believe that everyone should have access to powerful and user-friendly technology. That's why we're committed to creating products that respect your privacy, give you back control, and champion openness and accessibility.

That's why Gnoppix will always be free and open source. We believe that everyone should have the right to use, modify, and share our software without restriction.

To reward and celebrate those who support our mission, we created Gnoppix Pro. It brings together the most advanced features and the best open source software so you can unleash the full potential of your computer.

## When you buy Gnoppix, you're not just buying a product, you're supporting a mission.

Every purchase or donation helps us to continue developing Gnoppix Linux, contributing to open source projects, and creating products and services that make Linux more accessible to everyone.

Because we're funded entirely by the community, we're able to put you—the user—first in everything we do. That means we're focused on creating a Linux distribution that is easy to use, powerful, and secure.

We're grateful for the support of our community, and we're committed to continuing to make Gnoppix Linux the best Linux distribution possible.


{% assign posts = site.posts | sort: "date" | sort: "updated" | reverse %}

{% for post in posts %}
    {% include posts-listing.html post=post %}
{% endfor %}
