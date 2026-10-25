identify assets in the architecture, their purpose, and their relative value. These become the targets for would-be attackers. Next, they identify possible attackers and what they would want from the system:

+   - Who are your actual or likely adversaries?
+   - What do they want to achieve?
+   - What are their skills and resources?
+   - How determined are they?
+   - What would they be willing to risk or give up to achieve their goals?
+   - What about insiders?

As you collect these across projects, you can also build a reusable catalog of attack profiles with enough details to make them suitable for anyone who wants to conduct threat modeling.

Next, imagine that you are one of those adversaries and try to see your network *through their eyes*. You know what you want; how would you try to get at it by misusing the application?

Just like the product backlog and user stories, a threat model is a living document—as you change the design, you need to go back and update your threat model to see if any new threats appear.

# 9.5.1.2 Risk Analysis and Assessment

For Step 5 of the recipe, we turn to another mnemonic from Microsoft, called DREAD, described in Section 4.3.3.4. It scores 5 categories, which are added together and divided by 5, yielding a result from 0 to 10, where 0 indicates little or no impact and 10 is the house-on-fire situation.

Other risk analysis considerations include:

+   - Threats and vulnerabilities that exist in the project’s environment or that result from interaction with other systems.
+   - Code that was created by external development groups in either source or object form. It’s vitally important to carefully evaluate any code from sources external to your team, including purchased libraries and open-source components and libraries that may be present. Failing to do so might cause security vulnerabilities the team does not know about or learns about too late.
+   - Threat models should include all legacy code if the project is a new release of an existing program. Such code could have been written before much was known about software security and, therefore, likely contains vulnerabilities.
+   - A detailed privacy analysis to document your project’s key privacy aspects. Important issues to consider include:
+     - What personal data is collected?
+     - What is the compelling customer value proposition and business justification?
+     - What notice and consent experiences are provided?
+     - What controls are provided to both internal and external users of the application?
+     - How is unauthorized access to personal information prevented?