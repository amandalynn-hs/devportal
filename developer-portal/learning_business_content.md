# Learning API for Business _DRAFT_
## Purpose
The purpose of this API to act as a public-facing API providing CRUD operations for assignments and other data objects in the HealthStream Learning Center (HLC). It acts as a proxy for other internal-only APIs and contains no business logic.

## Use Cases
<span style="color:Blue;"><b><i>Add use cases based on Business and Technical/Architect level</b></span>

<span style="color:Crimson;"><b> - This API provides user(student)information as available in HealthStream Learning Center(HLC). It allows us to modify or even delete student information, without logging into HLC.Any update made to student information is real time.
- A system or process wants to make select course assignments without using the HealthStream Learning Center (HLC) interactive application. Uses: external course recommender, course ordered from online store.</b></span>
- ~~A system or process will manage a student profile rather than using the HLC or Data Imports.~~ <span style="color:Crimson;"> <b><i>Not Valid needs to be removed</b></span>
- Support for create, read, update, delete operations.
<span style="color:Crimson;"><b></b></span>

## Technology
<span style="color:Blue;"><b><i>Add use cases based on Business and Technical/Architect level </b></span>

Learning API is a relatively standard ASP.NET Core Web API that relies primarily on controllers and models but also implements interfaces and clients for its four services.

<span style="color:Crimson;"><b>This is a secured API, where a secret key needs to be passed to allow authentication and authorization.</b></span>

There are five basic resources offered in the Learning API:

# Assignment

- <span style="color:Crimson;"><b> This endpoint allows API to create individual assignments in HLC. This also allows ability to modify and delete those assignments. As part of request body, the api would need, valid course id (a unique identifier, created at time of course creation), start date of assignment and due date of assignment.  </b></span>

* Some of the other benefits of this api
* This also allows us to create institution specific assignments.
* It allows turns on setting of reassigning the course if user fails courses. 


# hStream 
<span style="color:Crimson;"><b> The endpoint returns NRP credential details for an HLC user, who has a verified hStream Id. This endpoint returns, NRP card expiration and status.</b></span>
- Organization<span style="color:Crimson;"><b> When we pass a unique identifier for an organization, this endpoint returns Name of organization as in HLC.</b></span>
# User
<span style="color:Crimson;"><b>
Once a user is created in HLC, i.e. either via imports or via profile/student API or even if user creates it by logging into HLC as admin, etc, this API provides user(student)</b></span>
# Status
<span style="color:Crimson;"><b>We at HealthStream take our system uptime very seriously. But things happen over http :(. The status endpoint provide information about API being up and functional or if API is up or having issues. This can be useful if consuming application continues to get error during retry. In such scenario a quick check to status endpoint would allow us to identity if there is an issue with API itself.
There is also a version endpoint. We can refer [release notes](http://google.com) for version details of our minor and patch versions. We ensure our version changes are backwards compatible allowing consuming application to not worry about it. However, in scenario when there is a major version or a breaking change is introduced, we will communicate with all consuming parties.</b></span>

Each resource is supported by a controller and model.
As such, it functions as a standard RESTful API.