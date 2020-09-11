
# Table of Contents

1.  [CI Signal on-boarding script](#orgf457f2a)
    1.  [Video 1 CI Overview - for beginners, can be skipped](#org37a6774)
        1.  [What is Continuous Integration?](#orged880e9)
        2.  [What is the Signal that we are looking for?](#org85a24cb)
        3.  [What is the noise that disrupts the CI Signal?](#orgb8aa480)
    2.  [Video 2 The Kubernetes CI Signal Team - Overview / benefits of participating](#orgfc777be)
    3.  [Video 3 How Continuous Integration is run on the Kubernetes Project](#org8fea538)
    4.  [Video 4 Day-to-day work of the Kubernetes CI Signal Team](#org0c69f63)
    5.  [Video 5 How CI Signal Team work with Test Infra](#org446a551)
        1.  [What does the CI-Signal Team do?](#org5693ffe)
        2.  [Using test-grid to find flaky tests on kubernetes?](#org26e6940)
        3.  [How to report a flaky test](#org24e7d83)
        4.  [Why participate in the CI Signal Team?](#orgbf0bb1d)
    6.  [What is a flaky test?](#orgbb93dcd)


<a id="orgf457f2a"></a>

# CI Signal on-boarding script


<a id="org37a6774"></a>

## Video 1 CI Overview - for beginners, can be skipped


<a id="orged880e9"></a>

### What is Continuous Integration?

[Continuous Integration (CI)](https://en.wikipedia.org/wiki/Continuous_integration) is at the core of all modern software development.

Every time a new code change is submitted to the project we want to integrate
those changes into the project as quickly as possible.

Integrating new code changes happens continuously as developers submit Pull
Requests on Github.

However, in order to ensure the stability of the existing code base there are
jobs that run tests automatically when a PR is submitted.


<a id="org85a24cb"></a>

### What is the Signal that we are looking for?

When we talk about "CI Signal" we are referring to the evidence provided by
running tests on a new code change that allows us to make either of the following determiniations:

"Yes, this new code can be safely integrated into our code base!" 

or

"No, this new code needs to be changed further in some way"


<a id="orgb8aa480"></a>

### What is the noise that disrupts the CI Signal?

Sometimes, tests run as part of CI, intermittently flip between failing and
succeeding in a non-deterministic way.

Ideally, a test should fail only when there is a problem with the code being tested. 
That is the Signal that we need.

Tests that provide inconsistent results for the same code commit and the same
infrastructure commit are called falky tests. 

From [Eradicating Non-Determinism in Tests by Martin Fowler](https://martinfowler.com/articles/nonDeterminism.html#:~:text=A%20test%20is%20non%2Ddeterministic,such%20tests%20are%20seemingly%20random).

> A test is non-deterministic when it passes sometimes and fails sometimes,
> without any noticeable change in the code, tests, or environment. Such tests
> fail, then you re-run them and they pass. Test failures for such tests are
> seemingly random.


<a id="orgfc777be"></a>

## Video 2 The Kubernetes CI Signal Team - Overview / benefits of participating


<a id="org8fea538"></a>

## Video 3 How Continuous Integration is run on the Kubernetes Project


<a id="org0c69f63"></a>

## Video 4 Day-to-day work of the Kubernetes CI Signal Team


<a id="org446a551"></a>

## Video 5 How CI Signal Team work with Test Infra


<a id="org5693ffe"></a>

### What does the CI-Signal Team do?

On the Kubernetes Project, the CI Signal Team is assembled on a per-release basis.

We eliminate noise from the code quality signal provided by the Continuous Integration jobs

The CI Signal team seek out flaky tests and reports them as Github Issues to the wider Kubernetes community so that we can eradicate non-deterministic test results.

### Using test-grid to find flaky tests on Kubernetes

Test Grid is a CI result presentation tool that is the starting point for
reviewing tests results on kubernetes, The summary page of the
master-blocking and master-informing tests on test-grid will report you when
a CI job has flaky tests

From there you can drill down into the job that contains the flaky tests.

And on the job page can  

-   sort the tests by flakiness
-   see how the test results change over each run
    -   green - test passed
    -   red - test fails
    -   white - test did not run
-   review the git commit ids of both the Kubernetes code AND the underlying CI infrastructure which includes Prow.
-   zoom out to see more test results
-   review the change in runtime durations Jobs over time


<a id="org24e7d83"></a>

### How to report a flaky test

There is existing content on this. dig out 


<a id="orgbf0bb1d"></a>

### Why participate in the CI Signal Team?

There are many great resaons to work on the CI Signal team for a release cycle.

CI Signal work can be viewed as useful stepping stone to becoming a Kubernetes contributor.

    You will get to work with and meet the rest of the Release team who are fun to work with and know a lot about Kubernetes.
    By reporting flaky tests you will get to interact with Special Interest Groups and meet active contributors there and 
perhaps figure

1.  How Continuous Integration works on Kubernetes

    This is no small undertaking, there are mulitple components involved in CI on Kubernetes
    Here are the main components involved in testing new changes to the Kubernetes project
    
    1.  Prow - CI Server
    
          The CI Server for the Kubernetes is a generally referred to as Prow which
        is made up of several components. 
        Prow Status <https://prow.k8s.io/?job=pull-kubernetes-e2e-gce-network-proxy-http-connect>
    
    2.  Testgrid - CI Results
    
        Job Runtime duration <https://testgrid.k8s.io/presubmits-kubernetes-blocking#pull-kubernetes-e2e-gce-network-proxy-http-connect&graph-metrics=test-duration-minutes>
    
    3.  Hound - Code Search
    
        [Hound](https://cs.k8s.io/)
    
    4.  GCP - Goolge Cloud where CI runs
    
    5.  Triage - Tool that Agregates test failures accross CI Job
    
        <https://go.k8s.io/triage>
        <https://storage.googleapis.com/k8s-gubernator/triage/index.html?pr=1&job=pull-kubernetes-e2e-gce-network-proxy-http-connect>
    
    6.  Triage Party

2.  Learn how the Kubernetes project is structured

    Changes to the Kubernetes code base are carried out by individual Special
    Interest Groups (SIGs) Working on CI Signal allows you to meet and 
    interact with existing SIG contributors while you familiarise your self with the 
    work that they do from a testing perspective.
    
    For each release cycle we hunt for flaky tests, log those tests as issue on
    github, coordinate and participate in triage of the tests that are producing
    non-deterministic results.

3.  Discover where in the Kubernetes Projects


<a id="orgbb93dcd"></a>

## What is a flaky test?

From [Eradicating Non-Determinism in Tests by Martin Fowler](https://martinfowler.com/articles/nonDeterminism.html#:~:text=A%20test%20is%20non%2Ddeterministic,such%20tests%20are%20seemingly%20random).

    A test is non-deterministic when it passes sometimes and fails sometimes,
    without any noticeable change in the code, tests, or environment. Such tests
    fail, then you re-run them and they pass. Test failures for such tests are
    seemingly random.
\#+end<sub>quote</sub>

