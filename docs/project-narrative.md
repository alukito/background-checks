---
id: project-narrative
title: Welcome to the background-checks project
description: TODO
sidebar_label: Introduction
---

## What is the goal of this project?

The goal of this project is to teach you, the developer, how to think about building Temporal Applications that have Long Running Human Driven Workflows using a Temporal SDK, by leading you through a comprehensive implementation within the context of a real-life use case.

## What is a Long Running Human Driven Workflow?

A Long Running Human Driven Workflow is a Temporal Workflow Execution that could be Running (be in an Open state) for hours, days, weeks, or even years, and requires input from a real person to progress.

## What is the real-life use case?

Checkr launched in 2014 and has since become the leading tech company in the Background Check industry.
Checkr’s intention is to make Background Checks fast, easy, and efficient for countries around the world.

A [Temporal case study from October, 2020](https://docs.temporal.io/blog/how-temporal-simplified-checkr-workflows) touches on the demand for automated Background Checks due to a surge in gig economy employment, and the interesting problem space that presented itself as demand scaled.

Depending on the type of employment, the needs of a Background Checks for any given Candidate can vary.
Often a single Background Check will result in a dozen individual Searches for information.
Sometimes the only way to conduct or get the results of a Search is by taking a manual step, like making a phone call or uploading a file.

Some of the more common Searches in a Background Check include:

- SSN trace for known aliases and addresses
- Federal criminal records check
- State criminal records check
- County civil records check
- County criminal records check
- Municipal criminal records check
- Employment verification
- Education verification
- Motor vehicle history
- Drug & health screen

If the Candidate (subject of the Background Check) is associated with multiple addresses, then multiple state level, county level, and municipal level Searches could occur.
Some of the Searches can be done against public facing databases, others may require parsing PDFs or images.
With each individual Search, there is an opportunity for something to happen that can cause a delay.

Checkr needed to have solutions for problems like having a large volume of long-running business processes (hours, days, weeks) that often need to fall back to a human for input, communicating with thousands of external endpoints that are used to query for information, and correlating a large volume of messages from a variety of unreliable sources.

### How did Checkr solve these problems before Temporal?

To address those problems Checkr implemented a complex state machine using stand alone databases, Kafka queues, and micro-services.

But this approach introduced its own set of problems.

- Testing and applying updates and features to the live system was very hard, and there were no official means by which to do it.
- New engineers needed to understand the entire Checkr specific state machine architecture, regardless of the team or area they were working on.
- Even when things went as expected, the percentage of issues and failures at that scale meant that it was not reliable as desired.

Checkr understood that something needed to change to their approach and started looking for solutions.
In their search, they came across the Temporal Platform.

### Why is the Temporal Platform a great fit for this use case?

Code based workflows appeal to developers.
Business processes (Background Checks) map directly to Workflow functions.
This results in a very close mapping of business requirements to code and vice versa.

The Temporal Platform has built in support to handle a wide set of failures so there isn’t a need to maintain infrastructure for that purpose.

Code is testable, and the Temporal Platform provides out-of-the-box Workflow function and Activity function testing capabilities while still enabling developers to use their existing testing and mocking frameworks to write unit and integration tests for mission critical code.

Cancelling a Background Check and rolling back state (compensation) is defined within the Workflow code.

It has built in debugging and troubleshooting tools such as “replays” that allow developers to step through an execution to see what happened.

The Temporal Platform is designed to support business processes that could span decades, so maintaining the complex state of a Background becomes far more trivial

And the Temporal Platform has built in Visibility APIs and to view the status and get the state of a given Workflow Execution at any time, as well as metric endpoints to monitor the health of the platform.

## What are the technical concepts introduced in this project?

The following concepts are introduce in this project:

- [Temporal Client](#)
- [Workflow Definition](https://docs.temporal.io/docs/content/what-is-a-workflow-definition)
- [Workflow Execution](https://docs.temporal.io/docs/content/what-is-a-workflow-execution)
- [Workflow Type](https://docs.temporal.io/docs/content)
- [Workflow Id](https://docs.temporal.io/docs/content/what-is-a-workflow-id)
- [Workflow Id Reuse Policy](https://docs.temporal.io/docs/content/what-is-a-workflow-id-reuse-policy)
- [Child Workflow Execution](https://docs.temporal.io/docs/content/what-is-a-child-workflow-execution)
- [Activity Definition](https://docs.temporal.io/docs/content/what-is-an-activity-definition)
- [Activity Execution](https://docs.temporal.io/docs/content/what-is-an-activity-execution)
- [Worker](https://docs.temporal.io/docs/content/what-is-a-worker)
- [Task Queue](https://docs.temporal.io/docs/content/what-is-a-task-queue)
- [Advanced Visibility](https://docs.temporal.io/docs/content/what-is-advanced-visibility)
- [List Filters](https://docs.temporal.io/docs/content/what-is-a-list-filter)
- [Search Attributes](https://docs.temporal.io/docs/content/what-is-a-search-attribute)
- [Custom Data Converter](https://docs.temporal.io/docs/content/what-is-a-data-converter)
- [Temporal Web UI](#)

## What are the technical how-tos introduced in this application?

The following development "how-tos" provide a foundation for the development patterns expressed in this project:

- [How to develop a Workflow Definition in Go](https://docs.temporal.io/docs/go/how-to-develop-a-workflow-definition-in-go)
- [How to spawn a Workflow Execution in Go](https://docs.temporal.io/docs/go/how-to-spawn-a-workflow-execution-in-go)
- [Getting the result of a Workflow Execution in Go](https://docs.temporal.io/docs/go/how-to-get-the-result-of-a-workflow-execution-in-go)
- [How to send a Cancellation Request to a Workflow Execution in Go](https://docs.temporal.io/docs/go/how-to-request-cancellation-of-a-workflow-execution-in-go)
- [How to send a Signal to a Workflow Execution in Go](#)
- [How to handle a Signal in a Workflow in Go](#)
- [How to send a Query to a Workflow Execution in Go](#)
- [How to handle a Query in a Workflow in Go](#)
- [How to set StartWorkflowOptions in Go](https://docs.temporal.io/docs/content/how-to-set-startworkflowoptions-in-go)
- [How to spawn an Activity Execution in Go](https://docs.temporal.io/docs/go/how-to-spawn-an-activity-execution-in-go)
- [How to spawn a Child Workflow Execution in Go](https://docs.temporal.io/docs/go/how-to-spawn-a-child-workflow-execution-in-go)
- [How to set ActivityOptions in Go](https://docs.temporal.io/docs/go/how-to-set-activityoptions-in-go)
- [How to develop a Workflow Program in Go](https://docs.temporal.io/docs/how-to-develop-a-worker-program-in-go)
- [How to provide a custom Data Converter in Go](#)
