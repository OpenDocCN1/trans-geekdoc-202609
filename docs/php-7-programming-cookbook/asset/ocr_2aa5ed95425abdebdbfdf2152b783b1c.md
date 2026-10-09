# # 8  
Working with Date/Time and International Aspects

In this chapter, we will cover the following topics:

+   - Using emoticons or emoji in a view script
- Converting complex characters
- Getting the locale from browser data
- Formatting numbers by locale
- Handling currency by locale
- Formatting date/time by locale
- Creating an HTML international calendar generator
- Building a recurring events generator
- Handling translation without gettext

# ## Introduction

We will start this chapter with two recipes that take advantage of a new **Unicode** escape syntax introduced with **PHP 7**. After that, we will cover how to determine a web visitor’s **locale** from browser data. The next few recipes will cover the creation of a locale class, which will allow you to represent numbers, currency, dates, and time in a format specific to a locale. Finally, we will cover recipes that demonstrate how to generate an internationalized calendar, handle recurring events, and perform translation without having to use `gettext`.