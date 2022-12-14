

 Status                 | In Progress                                                      |
| ---------------------- | ---------------------------------------------------------------- |
| Date of Request        | Date when the request was made                                   |
| Date of Implementation | Deadline for implementation of design to fulfill the requirement |
| Domain                 | Name of the domain for which the design applies.                 |
| Program                | Name of the program which will implement the design              |
| Architect              | Name of the Architect working on the design                      |
| Development Team       | Name of the developers or the team involed                       |
| Approver               | Name of the approver or the Board                                |
| Contributors           | Name of the people who have contributed to this architecture     |
| Final Review Outcome   | Approved or Rejected                                             |
| Approval Date          | Date when the design was approved                                |
| Decision Type          | Approved or Conditionally approved or Rejected                   |
| Technical Debt, if any | Yes or No. If yes, add the details below                         |

Table of Contents
=================
- [Table of Contents](#table-of-contents)
- [Objective](#objective)
- [Expectation from the review Board](#expectation-from-the-review-board)
- [Solution Design Options](#solution-design-options)
- [Comparison and final Recommendation](#comparison-and-final-recommendation)
- [Final Recommendation](#final-recommendation)
- [Open Questions or Concerns](#open-questions-or-concerns)
- [Technical Debts](#technical-debts)
- [Piece of Advice](#piece-of-advice)

# Objective 

Why do you want to write this solution design document? What is the problem you want to solve?

# Expectation from the review Board 
Be very clear about what you expect from the members of the review board if you are presenting your design to an audience that needs to approve it. That helps keep the audience focussed and not propel them into unnecessary discussions and also provides them a clear idea of what to look for or observe in the design.
- Approval ask 1
- Approval ask 2
- Approval ask 4

# Solution Design Options 
Present all the options on the table with the pros and cons of each option

**Option 1**

- **High Level Design**

  In this section provide a clear explaination of your design with a flow diagram or an image created using either draw.io or lucidchart or visio. Keep it low on text and heavy on visual representation. 

- **Privacy and Security**

  Your design document should clearly highlight how the security aspects will be taken care of if it is a new design. For a change in the existing design, you must clearly specify the aspects which might get impacted from a security standpoint and how you intend to take care of them. In a nutshell, follow the principle of “Security by Design”. You must explain platform security, data security, authentication, and authorization mechanisms.
  Another really important aspect that the design must cater to is the classification of the data that will be processed and how will your access management framework cater to it.

- **Availability**

  In production, solutions catering to critical business requirements are expected to have high uptime and availability. You must clearly design how you would take care of this requirement and what would happen if your application suffers an outage due to platform issues. For instance, what would happen if there is an outage in the data center where your database is hosted? Will there be a failover to a database in a different data center in a different region?

- **Resiliency**

  Trust me, over the years I have seen these two things to be the most underrated functionalities in design documents when it comes to the Data domain. Always explain how the way your application would be restarted if there is a failure and what would happen when it is restarted. Is there a checkpoint from where it has to be started or does it have to start from scratch? Also important is to explain what would happen if the database crashes or get corrupts. Will there be daily backups and how will you restore the database to the point in time where it crashed? Always make sure you consider this scenario in your design.
- **Scalability**
 
  Scalability is the ability of a system to handle increased. Your design must be very scalable and can respond to the increase of decrease in demand. Hence your design must consider scalability both in terms of the platform as well as an increase in data loads. For example, if your daily loads are deltas and not very large but month-end loads are a full large load you could consider autoscaling where the platform can have more computational power on month-end and automatically scale back to a lower configuration for the rest of the month. Scalability automatically impacts the operational efficiency and cost impact of your design.
- **Observability**
 
  It is very important to detail how your design will support observability in terms of monitoring, logging, and auditing. This part of the solution design should also detail the kind of alerts which will be configured and the corresponding actions against an alert. As part of observability, I also consider Data Quality. If your design is about loading data into a data platform you need to ensure that all critical data elements have been identified and that
- **Extensibility**
 
  This section is relevant mostly in designs that have to deal with data engineering or code development. For instance, if your design is about extracting data from source systems into your data platform you must highlight how would your code look like and adhere to the principles of software engineering, and will be modular and reusable.
- **Deployment**
 
  This section of the design document comes into play in almost all aspects whether it is Platform, Data Engineering, Data Modeling, or Data Visualization. Whatever is being built or developed has to be deployed and your design should have clear instructions on how it should be done and must take into account how automated testing, deployment, CI/CD, deployment of the database, and deployment of reports would look like.
- **Latency and Orchestration**
 
  As part of your solution design, it is very important to highlight the consistency of your data loads. The latency of data needed by the business users in the end product and the frequency of data loads into the platform must be clearly defined so that the development team can configure orchestration for the loads.
- **Performance considerations**
 
  Again, performance is one of the most underrated aspects in a design document and that bites in the end when you have deployed your solution in production and is ready for the real world. You must clearly highlight expected performance bottlenecks and ways development teams must solve them. Details about the volume of data loads, network bandwidth, partitions, and indexes as part of the design come in handy when the solution is being deployed in production.
- **Cost Considerations**
 
  Cost is THE MOST important aspect of any solution design document and something which I have seen in the world of Cloud not being considered. A big mistake and you should absolutely avoid it. Review boards must reject any solution design which does not have a cost-impact analysis. You must clearly highlight the cost impact of every new component being introduced into the architecture and the impact on the cost due to any proposed changes to the existing design. Consider the volume of data loads, the computation aspects, data loading frequencies, movement of data outside and inside your network, operational cost, etc. into account when you create any design. Again never ever miss this part of your design. Also would be advisable to make part of the design the ways in which costs can be optimized.
- **Governance**
 
  The design document must clearly highlight the ownership aspect of the platform, the application, and the data residing within the application. Clear ownership must be defined in terms of who owns the application, who owns the data, who owns the platform, and what should be the standard operating protocol when there is an issue in either the application, data, or platform. This is something that I have seen not be considered well in advance as part of the design and we end up with orphan applications in production.
# Comparison and final Recommendation 
If your design document has multiple options, it is also better to have a comparision table to help the readers of your design easily understand the difference and your recommendations. 

Creating a table in markdown is very difficult. What I normally do is, I create it in excel and use an online tool to convert that excel to markdown. I normally use [Excel to Markdown](https://tabletomarkdown.com/convert-spreadsheet-to-markdown/ ) for this purpose.It is free and very easy to use. 

| Assessment Criterias       | Option 1     | Option 2     | Option 3     |
| -------------------------- | ------------ | ------------ | ------------ |
| Availability               | Pros<br>Cons | Pros<br>Cons | Pros<br>Cons |
| Resiliency                 | Pros<br>Cons | Pros<br>Cons | Pros<br>Cons |
| Scalability                | Pros<br>Cons | Pros<br>Cons | Pros<br>Cons |
| Observability              | Pros<br>Cons | Pros<br>Cons | Pros<br>Cons |
| Extensibility              | Pros<br>Cons | Pros<br>Cons | Pros<br>Cons |
| Deployment                 | Pros<br>Cons | Pros<br>Cons | Pros<br>Cons |
| Latency and Orchestration  | Pros<br>Cons | Pros<br>Cons | Pros<br>Cons |
| Performance considerations | Pros<br>Cons | Pros<br>Cons | Pros<br>Cons |
| Cost Considerations        | Pros<br>Cons | Pros<br>Cons | Pros<br>Cons |
| Governance                 | Pros<br>Cons | Pros<br>Cons | Pros<br>Cons |
| Other considerations       | Pros<br>Cons | Pros<br>Cons | Pros<br>Cons |
| Final Recommendation       | No           | No           | Yes          |

# Final Recommendation
Explain what your final recommendation and a summary of why you recommend a particular option. Please make sure not to have a biased opinion. 

# Open Questions or Concerns 
Its always advisable to clearly highlight if you have any open questions or concerns which you would like to address before implemting the design. 
- Question 1
- Question 2
- Question 3

# Technical Debts 
| Debt Detail | Possible Date when the debt will be solved | Owner |
| ----------- | ------------------------------------------ | ----- |
| Debt 1      |                                            |       |
| Debt 2      |                                            |       |
| Debt 3      |                                            |       |
|             |                                            |       |

# Piece of Advice
- Don’t get into the trap of “bigger the better”. My advice is to keep the design document brief, very clear, and must have only relevant information.
Refrain from writing designs using power points and word documents. In my experience using markdown files as part of Github, Azure Wiki, or tools like Notion and Confluence is better where the design is presented more like a blog page rather than a multi-pager boring word document or PowerPoint presentation.
- A picture speaks more than a thousand words. Always trying to express your thought in a solution design rather than lots of text. Trust me now one reads a text busy design.
- Leverage the power of versioning tools like Github and Azure Repo to maintain your designs. GitHub pages, readme files, or code wikis are really very handy where you can commit your markdown files to the repository branches and review them using pull requests. It really instills discipline within an architecture team.