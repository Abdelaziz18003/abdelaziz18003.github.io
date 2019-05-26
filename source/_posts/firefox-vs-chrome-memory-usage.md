---
title: "Firefox vs Chrome: Memory usage"
date: Mon Dec 17 2018 14:19:01 GMT+0100
description: At the end of 2017, Mozilla introduced Firefox Quantum the blazing fast, completely reinvented Firefox. It was shipped with a new beautiful look and the speed compared to it's previous versions was obvious.
photos:
  - /img/chrome-vs-firefox.jpg
---

![Chrome vs Firefox image](/img/chrome-vs-firefox.jpg)

At the end of 2017, Mozilla introduced Firefox Quantum the blazing fast, completely reinvented Firefox. It was shipped with a new beautiful look and the speed compared to it's previous versions was obvious. One of Mozilla's claims too was the less usage of memory compared to Google Chrome. For a Firefox user like me, this was great news. I was able to notice the speed and enjoy the new design. But, I didn't pay attention to how it compares to Chrome in memory usage.

Recently I read a [blog post](https://www.businessinsider.com/google-chrome-vs-firefox-performance-memory-2018-7#1-get-chrome-to-its-purest-form-minus-your-profile-any-extensions-or-other-things-that-could-affect-the-result-9) saying that Firefox consumes more RAM than Chrome. This was not what Mozilla claimed a year ago, I felt betrayed. I started searching for other blog posts with other benchmarks. But, I found different answers with different results. So, I decided to do my own tests.

## Making some tests

These tests are made in the following environment.

```yaml
OS: Ubuntu 18.04
RAM: 8 GB
Firefox: 64
Chrome: 70
```

After closing all the third party applicatins on my computer, I opened the Ubuntu `System Monitor` to see how much memory was in use. The initial memory usage was:

```yaml
memory: 2.1 GiB
```

Then I opened 30 tabs of 3 different websites in each browser while the other is closed. I used the `Guest Mode` in chrome and the `Safe Mode` in Firefox ( by going to `menu > help > Restart with add-ons disabled`) in order to get rid of any effects of installed add-ons.

The opened tabs was the following:

* **Test 1**: [The 30 top answers of Jon Skeet on Stackoverflow.](https://stackoverflow.com/users/22656/jon-skeet?tab=answers)

* **Test 2**: [The 30 first pages of HTML tutorial on w3schools.](https://www.w3schools.com/html/default.asp)

* **Test 3**: [30 Quasar-framework components' documentation pages (Field > Dialog).](https://quasar-framework.org/components/)

* **Test 4**: 20 different websites from the most famous ones (google, youtube, medium ...etc).

## Results

After the complete loading of the 30 tabs each time, I was opening the `System Monitor` to see the total memory usage. knowing the total memory makes it easy to deduce the consumption of each browser. It is as easy as subtracting the initial value of used memory from the new one (I calculated it this way because Chrome opens a lot of processes in Ubuntu and it is hard to keep adding them up). The consumed memory values corresponding to each browser are shown in the table below.

|             | Firefox   | Chrome    |
|:-----------:|:---------:|:---------:|
| **Test 1**  |  1.0 GiB  |  1.3 GiB  |
| **Test 2**  |  1.3 GiB  |  2.7 GiB  |
| **Test 3**  |  1.2 GiB  |  2.1 GiB  |
| **Test 4**  |  0.9 GiB  |  1.3 GiB  |

## Summary

The results above demonstrates that Firefox Quantum really uses less memory than Google Chrome, at least in my case. That supports Mozilla's claims about it's new kid. I shared here the results I got. But, I can not garantee that everybody else will get the same thing. Concerning the speed, I didn't make a real comparaison between the two. They are comparable in speed and I could not notice any difference in usage. Firefox nowadays is not the same Firefox couple of years ago.