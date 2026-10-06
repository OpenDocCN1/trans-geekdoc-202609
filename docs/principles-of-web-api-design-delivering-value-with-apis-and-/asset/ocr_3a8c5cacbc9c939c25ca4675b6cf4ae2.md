# SELECTING TOOLS TO ACCELERATE TESTING 229

the case. Instead, the UI tests the API as far as the UI exercises the API.
This means that if the UI is performing client-side validation of user input,
then UI tests would never verify the API’s ability to handle bad data.

While some may say that this level of testing is sufficient, they may be for-getting the recommendation of the Open Web Application Security Project
OWASP): do not trust user input. A user or client will not always submit
a a way that an API expects. Always validate the data that comes from
forms as well as from HTTP request headers.

One of the goals of API testing is to ensure that the API is able to handle a
mitude of good and bad values that may be submitted outside of a specific
UI. If we depend on UI tests, then the API should not be considered sufficient tested.

Another goal of API testing is to ensure that the API cannot be deployed
into production without passing tests. This requires API tests become
part of the continuous integration and delivery pipeline, just like all other
types of automated testing.

# Selecting Tools to Accelerate Testing

Some organizations may have an established quality assurance (QA) group that
specializes in automated testing and manual exploratory testing. QA teams may be
composed of those who write code and others who use testing tools that help
compose automation suites without the need to write code. Other organizations
may not have QA teams at all, instead relying on developers to write and
maintain API test code. These factors must be considered when selecting API testing
tools.

A number of open source and commercial testing tools are available today
the creation of API testing using API specification formats to help jumpstart
t testing process. Some are designed to support the creation of tests through a
UI to reduce or eliminate the need to write test code. Others are designed to offer
a scripting environment or test libraries that require coding. Be sure to select the right
solutions that match the testing preferences and skills found in the organization.

Performance and monitoring solutions, offered as third-party API monitoring-as-a-service, are available from a range of companies and often start as
a freemium service for a small number of tests. Open-source monitoring tools are
available that can be run on-premises or cloud-hosted infrastructure. Custom
tools built to perform load and performance testing can be modified to run less
frequently and at a smaller scale for the purpose of monitoring or soak testing.