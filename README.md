# Designing APIs with Swagger and Open API

- [Designing APIs with Swagger and Open API](#designing-apis-with-swagger-and-open-api)
  - [1 Introducing APIs and OpenAPI](#1-introducing-apis-and-openapi)
    - [1.1 What is an API ecosystem?](#11-what-is-an-api-ecosystem)
    - [1.2 Describing things](#12-describing-things)
      - [Bridget’s task](#bridgets-task)
      - [The potential of Bridget’s solution](#the-potential-of-bridgets-solution)
    - [1.3 What is OpenAPI?](#13-what-is-openapi)
      - [Example OpenAPI definition](#example-openapi-definition)
    - [1.4 Where do OpenAPI definitions fit in?](#14-where-do-openapi-definitions-fit-in)
    - [1.5 What is Swagger?](#15-what-is-swagger)
    - [1.6 What about REST?](#16-what-about-rest)
    - [1.7 When to use OpenAPI](#17-when-to-use-openapi)
      - [For API consumers](#for-api-consumers)
      - [For API producers](#for-api-producers)
      - [For API designers](#for-api-designers)
    - [1.8 This book](#18-this-book)
  - [2 Getting set up to make API requests](#2-getting-set-up-to-make-api-requests)
    - [2.1 The problem](#21-the-problem)
      - [armStall API overview](#armstall-api-overview)
      - [he first two operations of the FarmStall API](#he-first-two-operations-of-the-farmstall-api)
    - [2.2 Getting set up with Postman](#22-getting-set-up-with-postman)
    - [2.3 FarmStall API](#23-farmstall-api)
    - [2.4 Our first request](#24-our-first-request)
      - [Forming a GET request in Postman](#forming-a-get-request-in-postman)
      - [Verification](#verification)
    - [2.5 Adding a review to the FarmStall API](#25-adding-a-review-to-the-farmstall-api)
      - [Forming a POST request in Postman](#forming-a-post-request-in-postman)
      - [Verification](#verification-1)
    - [2.6 Practice](#26-practice)
      - [Cat (and other animal) facts API](#cat-and-other-animal-facts-api)
      - [Random avatar API](#random-avatar-api)
      - [DuckDuckGo’s search engine API](#duckduckgos-search-engine-api)
      - [Pirate talk API](#pirate-talk-api)
    - [2.7 HTTP for the brave](#27-http-for-the-brave)
  - [3 Our first taste of OpenAPI definitions](#3-our-first-taste-of-openapi-definitions)
    - [3.1 The problem](#31-the-problem)
    - [3.2 Introducing the OpenAPI specification](#32-introducing-the-openapi-specification)
    - [3.3 A quick refresher on YAML](#33-a-quick-refresher-on-yaml)
      - [From JSON to YAML](#from-json-to-yaml)
    - [3.5 Extending our first operation](#35-extending-our-first-operation)
  - [4 Using Swagger Editor to write OpenAPI definitions](#4-using-swagger-editor-to-write-openapi-definitions)
    - [4.1 Introducing Swagger Editor](#41-introducing-swagger-editor)
      - [he Editor panel](#he-editor-panel)
      - [he UI Docs panel](#he-ui-docs-panel)
      - [he toolbar](#he-toolbar)
      - [ersistence](#ersistence)
    - [4.2 Writing the smallest OpenAPI definition in Swagger](#42-writing-the-smallest-openapi-definition-in-swagger)
      - [Editor](#editor)
      - [The smallest valid OpenAPI definition](#the-smallest-valid-openapi-definition)
      - [Writing in Swagger Editor](#writing-in-swagger-editor)
      - [A word on validation](#a-word-on-validation)
    - [4.3 Adding GET /reviews to our definition](#43-adding-get-reviews-to-our-definition)
    - [4.4 Interacting with our API](#44-interacting-with-our-api)
      - [Executing GET /reviews](#executing-get-reviews)
      - [Adding servers to our definition](#adding-servers-to-our-definition)
      - [Executing GET /reviews (again)](#executing-get-reviews-again)
  - [5 Describing API responses](#5-describing-api-responses)
    - [5.1 HTTP responses](#51-http-responses)
    - [5.2 The problem](#52-the-problem)
    - [5.3 The mind-blowing world of data schemas](#53-the-mind-blowing-world-of-data-schemas)
    - [5.4 JSON Schema](#54-json-schema)
      - [The type field](#the-type-field)
      - [Adding a field to an object](#adding-a-field-to-an-object)
      - [The minimum and maximum keywords](#the-minimum-and-maximum-keywords)
      - [Number vs. integer](#number-vs-integer)
    - [5.5 Status codes](#55-status-codes)
    - [5.6 Media types (aka MIME)](#56-media-types-aka-mime)
    - [5.7 Describing the GET /reviews response](#57-describing-the-get-reviews-response)
      - [Smallest response in OpenAPI](#smallest-response-in-openapi)
      - [The GET /reviews 200 response body](#the-get-reviews-200-response-body)
      - [Adding the rating field to our response body](#adding-the-rating-field-to-our-response-body)
      - [Describing message, uuid, and userId](#describing-message-uuid-and-userid)
  - [6 Creating resources](#6-creating-resources)
    - [6.1 The problem](#61-the-problem)
    - [6.2 Describing POST /reviews with a request body](#62-describing-post-reviews-with-a-request-body)
      - [Where to find request bodies](#where-to-find-request-bodies)
      - [Describing the schema for POST /reviews requestBody](#describing-the-schema-for-post-reviews-requestbody)
    - [6.3 Executing operations with request bodies](#63-executing-operations-with-request-bodies)
      - [Adding examples to make try-it-out look pretty](#adding-examples-to-make-try-it-out-look-pretty)
    - [6.4 Describing GET /reviews/{reviewId} with a path](#64-describing-get-reviewsreviewid-with-a-path)
      - [parameter](#parameter)
      - [Path parameters](#path-parameters)
      - [Describing the reviewId path parameter](#describing-the-reviewid-path-parameter)
    - [6.5 Verifying our reviews are getting created](#65-verifying-our-reviews-are-getting-created)
  - [7 Adding authentication and authorization](#7-adding-authentication-and-authorization)
    - [7.1 The problem](#71-the-problem)
    - [7.2 Getting set up for authentication](#72-getting-set-up-for-authentication)
      - [Challenge: Describe POST /users](#challenge-describe-post-users)
      - [Challenge: Describe POST /tokens](#challenge-describe-post-tokens)
      - [Solution: Definition changes](#solution-definition-changes)
      - [Verifying we can create users and get a token](#verifying-we-can-create-users-and-get-a-token)
    - [7.3 Adding the Authorization header](#73-adding-the-authorization-header)
      - [How OpenAPI handles authorization](#how-openapi-handles-authorization)
      - [Types of authorization (securities) supported in OpenAPI 3.0.x](#types-of-authorization-securities-supported-in-openapi-30x)
      - [Adding the Authorization header security scheme](#adding-the-authorization-header-security-scheme)
      - [Adding the security requirements to POST /reviews](#adding-the-security-requirements-to-post-reviews)
      - [Using the security feature of try-it-out](#using-the-security-feature-of-try-it-out)
    - [7.4 Optional security](#74-optional-security)
    - [7.5 Other types of security schemas](#75-other-types-of-security-schemas)
    - [7.6 How to add security schemes in general](#76-how-to-add-security-schemes-in-general)
  - [8 Preparing and hosting API documentation](#8-preparing-and-hosting-api-documentation)
    - [8.1 The problem](#81-the-problem)
    - [8.2 Adding metadata to the definition](#82-adding-metadata-to-the-definition)
    - [8.3 Writing the description in Markdown](#83-writing-the-description-in-markdown)
      - [Markdown basics](#markdown-basics)
      - [Adding a rich text description to the FarmStall API definition](#adding-a-rich-text-description-to-the-farmstall-api-definition)
    - [8.4 Organizing operations with tags](#84-organizing-operations-with-tags)
      - [Adding the Reviews tag to GET /reviews](#adding-the-reviews-tag-to-get-reviews)
      - [Adding descriptions to tags](#adding-descriptions-to-tags)
      - [Adding the rest of the tags](#adding-the-rest-of-the-tags)
    - [8.5 Hosting our API documentation using Netlify.com and](#85-hosting-our-api-documentation-using-netlifycom-and)
      - [Swagger UI](#swagger-ui)
      - [Preparing Swagger UI with our definition](#preparing-swagger-ui-with-our-definition)
      - [Hosting on Netlify.com](#hosting-on-netlifycom)
    - [8.6 The end of part](#86-the-end-of-part)
      - [Part 2 Design-first](#part-2-design-first)
  - [9 Designing a web application](#9-designing-a-web-application)
    - [9.1 The PetSitter idea](#91-the-petsitter-idea)
    - [9.2 PetSitter project kickoff](#92-petsitter-project-kickoff)
      - [Additional requirements](#additional-requirements)
      - [Team structure](#team-structure)
      - [API-driven architecture](#api-driven-architecture)
      - [The plan](#the-plan)
    - [9.3 Domain modeling and APIs](#93-domain-modeling-and-apis)
      - [Domain modeling for APIs](#domain-modeling-for-apis)
      - [Looking back on FarmStall](#looking-back-on-farmstall)
    - [9.4 A domain model for PetSitter](#94-a-domain-model-for-petsitter)
      - [Concepts in the model](#concepts-in-the-model)
      - [The User model](#the-user-model)
      - [The Job and Dog models](#the-job-and-dog-models)
    - [9.5 User stories for PetSitter](#95-user-stories-for-petsitter)
      - [What are user stories?](#what-are-user-stories)
      - [Collecting user stories](#collecting-user-stories)
      - [Mapping user stories](#mapping-user-stories)
  - [10 Creating an API design using OpenAPI](#10-creating-an-api-design-using-openapi)
    - [10.1 The problem](#101-the-problem)
      - [onverting a domain model to OpenAPI](#onverting-a-domain-model-to-openapi)
      - [nsuring reusability](#nsuring-reusability)
    - [10.2 Creating the schemas](#102-creating-the-schemas)
      - [tarting an OpenAPI file with schemas](#tarting-an-openapi-file-with-schemas)
      - [eferencing common schemas](#eferencing-common-schemas)
      - [he User schema](#he-user-schema)
      - [he Job schema](#he-job-schema)
      - [he Dog schema](#he-dog-schema)
      - [he JobApplication schema](#he-jobapplication-schema)
    - [10.3 The CRUD approach to API operations](#103-the-crud-approach-to-api-operations)
      - [Defining API requests and responses](#defining-api-requests-and-responses)
      - [From user stories to CRUD design](#from-user-stories-to-crud-design)
    - [10.4 API operations for PetSitter](#104-api-operations-for-petsitter)
      - [User operations](#user-operations)
      - [Job operations](#job-operations)
      - [JobApplication operations](#jobapplication-operations)
  - [11 Building a change workflow around API design–first](#11-building-a-change-workflow-around-api-designfirst)
    - [11.1 The problem](#111-the-problem)
    - [11.2 Communicating and reacting to change](#112-communicating-and-reacting-to-change)
    - [11.3 GitHub as our workflow engine](#113-github-as-our-workflow-engine)
      - [A single source of truth](#a-single-source-of-truth)
      - [Suggesting a change](#suggesting-a-change)
      - [Agreeing on a change](#agreeing-on-a-change)
      - [A way of viewing changes (based on an older version)](#a-way-of-viewing-changes-based-on-an-older-version)
    - [11.4 Tying the GitHub workflow together](#114-tying-the-github-workflow-together)
      - [Setting up GitHub and the source of truth](#setting-up-github-and-the-source-of-truth)
      - [Steps in our GitHub workflow](#steps-in-our-github-workflow)
    - [11.5 A practical look at the workflow](#115-a-practical-look-at-the-workflow)
      - [Creating and suggesting DELETE /jobs/{id}](#creating-and-suggesting-delete-jobsid)
      - [Reviewing and accepting changes](#reviewing-and-accepting-changes)
      - [Comparing older branches to the latest](#comparing-older-branches-to-the-latest)
      - [What we’ve done](#what-weve-done)
  - [12 Implementing frontend code and reacting to changes](#12-implementing-frontend-code-and-reacting-to-changes)
    - [12.1 The problem](#121-the-problem)
    - [12.2 Setting up Prism](#122-setting-up-prism)
      - [Installing Prism](#installing-prism)
      - [Verifying that Prism works](#verifying-that-prism-works)
    - [12.3 Building a frontend based on a mock server](#123-building-a-frontend-based-on-a-mock-server)
      - [Adding multiple examples into your OpenAPI definition](#adding-multiple-examples-into-your-openapi-definition)
      - [Using examples in Prism](#using-examples-in-prism)
    - [12.4 Identifying a missing API operation](#124-identifying-a-missing-api-operation)
      - [Due diligence for adding the operation](#due-diligence-for-adding-the-operation)
      - [Designing the new operation](#designing-the-new-operation)
      - [Choosing which mock data response to get from Prism](#choosing-which-mock-data-response-to-get-from-prism)
      - [Formalizing and suggesting the change](#formalizing-and-suggesting-the-change)
      - [Extra curl examples](#extra-curl-examples)
  - [13 Building a backend with Node.js and Swagger Codegen](#13-building-a-backend-with-nodejs-and-swagger-codegen)
    - [13.1 The problem](#131-the-problem)
    - [13.2 Introducing Swagger Codegen](#132-introducing-swagger-codegen)
      - [Client code generation](#client-code-generation)
      - [Server code generation](#server-code-generation)
      - [Swagger Generator](#swagger-generator)
    - [13.3 The backend structure](#133-the-backend-structure)
      - [Generating the backend](#generating-the-backend)
      - [Investigating the structure](#investigating-the-structure)
      - [OpenAPI changes](#openapi-changes)
    - [13.4 Updating OpenAPI for the backend](#134-updating-openapi-for-the-backend)
      - [dding operation IDs](#dding-operation-ids)
      - [agging API operations](#agging-api-operations)
      - [egenerating the backend stubs](#egenerating-the-backend-stubs)
    - [13.5 Running and testing the backend](#135-running-and-testing-the-backend)
      - [Testing with Postman](#testing-with-postman)
      - [Testing input validation](#testing-input-validation)
      - [Output validation with Prism](#output-validation-with-prism)
    - [13.6 Database persistence with Mongoose](#136-database-persistence-with-mongoose)
      - [Another API modification](#another-api-modification)
      - [Getting ready to use MongoDB](#getting-ready-to-use-mongodb)
      - [Configuring Mongoose in the project](#configuring-mongoose-in-the-project)
      - [Creating models](#creating-models)
    - [13.7 Implementing API methods](#137-implementing-api-methods)
  - [14 Integrating and releasing the web application](#14-integrating-and-releasing-the-web-application)
    - [14.1 The problems](#141-the-problems)
      - [Authentication](#authentication)
      - [Organizing code](#organizing-code)
      - [Serving both components](#serving-both-components)
    - [14.2 Implementing authorization](#142-implementing-authorization)
      - [Creating a security scheme](#creating-a-security-scheme)
      - [Adding a “Login” action](#adding-a-login-action)
      - [Defining operation security](#defining-operation-security)
    - [14.3 Managing repositories](#143-managing-repositories)
      - [Keeping the existing structure](#keeping-the-existing-structure)
      - [Creating a shared Git repository to implement both components](#creating-a-shared-git-repository-to-implement-both-components)
      - [Combining code and API definition in a repository](#combining-code-and-api-definition-in-a-repository)
      - [Making the choice and refactoring](#making-the-choice-and-refactoring)
    - [14.4 Setting up an integrated web server](#144-setting-up-an-integrated-web-server)
      - [RL design](#rl-design)
      - [erver setup](#erver-setup)
      - [art 3 Extending APIs](#art-3-extending-apis)
  - [15 Designing the next API iteration](#15-designing-the-next-api-iteration)
    - [15.1 Reviewing the first development sprint](#151-reviewing-the-first-development-sprint)
    - [15.2 Planning the next sprint](#152-planning-the-next-sprint)
    - [15.3 Preparing for new features](#153-preparing-for-new-features)
      - [Reviewing the domain model](#reviewing-the-domain-model)
      - [Reviewing user stories](#reviewing-user-stories)
    - [15.4 Improving the developer experience](#154-improving-the-developer-experience)
      - [Consistency](#consistency)
      - [Error handling](#error-handling)
      - [Input validation](#input-validation)
      - [Versioning vs. evolvability](#versioning-vs-evolvability)
  - [16 Designing schemas with composition in OpenAPI](#16-designing-schemas-with-composition-in-openapi)
    - [16.1 The problem](#161-the-problem)
    - [16.2 Polymorphism and inheritance in domain models](#162-polymorphism-and-inheritance-in-domain-models)
    - [16.3 Updating the schemas](#163-updating-the-schemas)
      - [The Pet schema](#the-pet-schema)
      - [The Dog schema](#the-dog-schema)
      - [The Cat schema](#the-cat-schema)
    - [16.4 Polymorphism and inheritance in OpenAPI](#164-polymorphism-and-inheritance-in-openapi)
      - [Composition inside the Dog and Cat schemas](#composition-inside-the-dog-and-cat-schemas)
      - [Composition inside the Pet schema](#composition-inside-the-pet-schema)
    - [16.5 Adding discriminators in OpenAPI](#165-adding-discriminators-in-openapi)
  - [17 Scaling collection endpoints with filters and pagination](#17-scaling-collection-endpoints-with-filters-and-pagination)
    - [17.1 The problem](#171-the-problem)
    - [17.2 Designing filters](#172-designing-filters)
      - [Projection filters](#projection-filters)
      - [Selection filters](#selection-filters)
      - [Handling nested schemas](#handling-nested-schemas)
      - [Query languages](#query-languages)
      - [Special conventions](#special-conventions)
    - [17.3 Filters for PetSitter](#173-filters-for-petsitter)
      - [Finding filter fields](#finding-filter-fields)
      - [Adding filters to OpenAPI](#adding-filters-to-openapi)
      - [Making a request](#making-a-request)
    - [17.4 Designing pagination](#174-designing-pagination)
      - [Offset-based and page-based pagination](#offset-based-and-page-based-pagination)
      - [Cursor-based pagination](#cursor-based-pagination)
    - [17.5 Pagination for PetSitter](#175-pagination-for-petsitter)
      - [Adding pagination to OpenAPI](#adding-pagination-to-openapi)
      - [Extending our request example](#extending-our-request-example)
    - [17.6 Designing sorting](#176-designing-sorting)
      - [Single-field sorting](#single-field-sorting)
      - [Multifield sorting](#multifield-sorting)
      - [Consistency throughout parameter types](#consistency-throughout-parameter-types)
      - [17.7 Sorting for PetSitter](#177-sorting-for-petsitter)
      - [Finding sorting fields](#finding-sorting-fields)
      - [Designing the sort parameter](#designing-the-sort-parameter)
      - [Adding sorting to OpenAPI](#adding-sorting-to-openapi)
      - [The final request example](#the-final-request-example)
  - [18 Supporting the unhappy path: Error handling with problem+json](#18-supporting-the-unhappy-path-error-handling-with-problemjson)
    - [18.1 The problem](#181-the-problem)
    - [18.2 Error categories](#182-error-categories)
      - [Finding unhappy paths](#finding-unhappy-paths)
      - [Common error patterns](#common-error-patterns)
    - [18.3 Requirements for error responses](#183-requirements-for-error-responses)
    - [18.4 The OAS tools format](#184-the-oas-tools-format)
    - [18.5 The problem+json format](#185-the-problemjson-format)
    - [18.6 Adding error responses to OpenAPI](#186-adding-error-responses-to-openapi)
      - [Creating error schemas](#creating-error-schemas)
      - [Adding errors to operations](#adding-errors-to-operations)
    - [18.7 Error-handling guidance](#187-error-handling-guidance)
      - [rontend development](#rontend-development)
      - [ackend development](#ackend-development)
      - [9 Improving input validation with advanced JSON Schema](#9-improving-input-validation-with-advanced-json-schema)
  - [19.1 The problem](#191-the-problem)
    - [19.2 Supported validations](#192-supported-validations)
      - [Read-only and write-only properties](#read-only-and-write-only-properties)
      - [Enforcing number constraints](#enforcing-number-constraints)
      - [Enforcing string formats](#enforcing-string-formats)
      - [Enforcing array constraints](#enforcing-array-constraints)
      - [Defining enumerations](#defining-enumerations)
      - [Listing required and optional properties](#listing-required-and-optional-properties)
      - [Setting defaults](#setting-defaults)
    - [19.3 Updating PetSitter schemas](#193-updating-petsitter-schemas)
      - [User schema](#user-schema)
      - [Job schema](#job-schema)
      - [JobApplication schema](#jobapplication-schema)
      - [Pet, Dog, and Cat schemas](#pet-dog-and-cat-schemas)
  - [20 Versioning an API and handling breaking changes](#20-versioning-an-api-and-handling-breaking-changes)
    - [20.1 The problem](#201-the-problem)
    - [20.2 What is a breaking change?](#202-what-is-a-breaking-change)
    - [20.3 Releasing a breaking change](#203-releasing-a-breaking-change)
      - [Coordinated breaking changes](#coordinated-breaking-changes)
      - [Multiple API versions](#multiple-api-versions)
      - [Using media types to version operations](#using-media-types-to-version-operations)
      - [Adding and deprecating features](#adding-and-deprecating-features)
  - [21 The API prerelease checklist](#21-the-api-prerelease-checklist)
    - [21.1 Pros and cons of a public API](#211-pros-and-cons-of-a-public-api)
    - [21.2 The checklist](#212-the-checklist)
    - [21.3 Getting the API working](#213-getting-the-api-working)
      - [Unit testing your API](#unit-testing-your-api)
      - [End-to-end testing](#end-to-end-testing)
    - [21.4 Documentation](#214-documentation)
    - [21.5 Getting your API consistent](#215-getting-your-api-consistent)
    - [21.6 Validation and error reporting](#216-validation-and-error-reporting)
    - [21.7 An API roadmap and exposure index](#217-an-api-roadmap-and-exposure-index)
    - [21.8 Getting a change strategy](#218-getting-a-change-strategy)
    - [21.9 Improving security](#219-improving-security)
    - [21.10 Monitoring your API](#2110-monitoring-your-api)
      - [Setting up metric collection](#setting-up-metric-collection)
    - [21.11 Releasing the API](#2111-releasing-the-api)
  - [appendix A Swagger 2.0, OpenAPI 3.0, and OpenAPI 3](#appendix-a-swagger-20-openapi-30-and-openapi-3)

## 1 Introducing APIs and OpenAPI

### 1.1 What is an API ecosystem?

### 1.2 Describing things

#### Bridget’s task

#### The potential of Bridget’s solution

### 1.3 What is OpenAPI?

#### Example OpenAPI definition

### 1.4 Where do OpenAPI definitions fit in?

### 1.5 What is Swagger?

### 1.6 What about REST?

### 1.7 When to use OpenAPI

#### For API consumers

#### For API producers

#### For API designers

### 1.8 This book

## 2 Getting set up to make API requests

### 2.1 The problem

#### armStall API overview

#### he first two operations of the FarmStall API

### 2.2 Getting set up with Postman

### 2.3 FarmStall API

### 2.4 Our first request

#### Forming a GET request in Postman

#### Verification

### 2.5 Adding a review to the FarmStall API

#### Forming a POST request in Postman

#### Verification

### 2.6 Practice

#### Cat (and other animal) facts API

#### Random avatar API

#### DuckDuckGo’s search engine API

#### Pirate talk API

### 2.7 HTTP for the brave

## 3 Our first taste of OpenAPI definitions

### 3.1 The problem

### 3.2 Introducing the OpenAPI specification

### 3.3 A quick refresher on YAML

#### From JSON to YAML

### 3.5 Extending our first operation

## 4 Using Swagger Editor to write OpenAPI definitions

### 4.1 Introducing Swagger Editor

#### he Editor panel

#### he UI Docs panel

#### he toolbar

#### ersistence

### 4.2 Writing the smallest OpenAPI definition in Swagger

#### Editor

#### The smallest valid OpenAPI definition

#### Writing in Swagger Editor

#### A word on validation

### 4.3 Adding GET /reviews to our definition

### 4.4 Interacting with our API

#### Executing GET /reviews

#### Adding servers to our definition

#### Executing GET /reviews (again)

## 5 Describing API responses

### 5.1 HTTP responses

### 5.2 The problem

### 5.3 The mind-blowing world of data schemas

### 5.4 JSON Schema

#### The type field

#### Adding a field to an object

#### The minimum and maximum keywords

#### Number vs. integer

### 5.5 Status codes

### 5.6 Media types (aka MIME)

### 5.7 Describing the GET /reviews response

#### Smallest response in OpenAPI

#### The GET /reviews 200 response body

#### Adding the rating field to our response body

#### Describing message, uuid, and userId

## 6 Creating resources

### 6.1 The problem

### 6.2 Describing POST /reviews with a request body

#### Where to find request bodies

#### Describing the schema for POST /reviews requestBody

### 6.3 Executing operations with request bodies

#### Adding examples to make try-it-out look pretty

### 6.4 Describing GET /reviews/{reviewId} with a path

#### parameter

#### Path parameters

#### Describing the reviewId path parameter

### 6.5 Verifying our reviews are getting created

## 7 Adding authentication and authorization

### 7.1 The problem

### 7.2 Getting set up for authentication

#### Challenge: Describe POST /users

#### Challenge: Describe POST /tokens

#### Solution: Definition changes

#### Verifying we can create users and get a token

### 7.3 Adding the Authorization header

#### How OpenAPI handles authorization

#### Types of authorization (securities) supported in OpenAPI 3.0.x

#### Adding the Authorization header security scheme

#### Adding the security requirements to POST /reviews

#### Using the security feature of try-it-out

### 7.4 Optional security

### 7.5 Other types of security schemas

### 7.6 How to add security schemes in general

## 8 Preparing and hosting API documentation

### 8.1 The problem

### 8.2 Adding metadata to the definition

### 8.3 Writing the description in Markdown

#### Markdown basics

#### Adding a rich text description to the FarmStall API definition

### 8.4 Organizing operations with tags

#### Adding the Reviews tag to GET /reviews

#### Adding descriptions to tags

#### Adding the rest of the tags

### 8.5 Hosting our API documentation using Netlify.com and

#### Swagger UI

#### Preparing Swagger UI with our definition

#### Hosting on Netlify.com

### 8.6 The end of part

#### Part 2 Design-first

## 9 Designing a web application

### 9.1 The PetSitter idea

### 9.2 PetSitter project kickoff

#### Additional requirements

#### Team structure

#### API-driven architecture

#### The plan

### 9.3 Domain modeling and APIs

#### Domain modeling for APIs

#### Looking back on FarmStall

### 9.4 A domain model for PetSitter

#### Concepts in the model

#### The User model

#### The Job and Dog models

### 9.5 User stories for PetSitter

#### What are user stories?

#### Collecting user stories

#### Mapping user stories

## 10 Creating an API design using OpenAPI

### 10.1 The problem

#### onverting a domain model to OpenAPI

#### nsuring reusability

### 10.2 Creating the schemas

#### tarting an OpenAPI file with schemas

#### eferencing common schemas

#### he User schema

#### he Job schema

#### he Dog schema

#### he JobApplication schema

### 10.3 The CRUD approach to API operations

#### Defining API requests and responses

#### From user stories to CRUD design

### 10.4 API operations for PetSitter

#### User operations

#### Job operations

#### JobApplication operations

## 11 Building a change workflow around API design–first

### 11.1 The problem

### 11.2 Communicating and reacting to change

### 11.3 GitHub as our workflow engine

#### A single source of truth

#### Suggesting a change

#### Agreeing on a change

#### A way of viewing changes (based on an older version)

### 11.4 Tying the GitHub workflow together

#### Setting up GitHub and the source of truth

#### Steps in our GitHub workflow

### 11.5 A practical look at the workflow

#### Creating and suggesting DELETE /jobs/{id}

#### Reviewing and accepting changes

#### Comparing older branches to the latest

#### What we’ve done

## 12 Implementing frontend code and reacting to changes

### 12.1 The problem

### 12.2 Setting up Prism

#### Installing Prism

#### Verifying that Prism works

### 12.3 Building a frontend based on a mock server

#### Adding multiple examples into your OpenAPI definition

#### Using examples in Prism

### 12.4 Identifying a missing API operation

#### Due diligence for adding the operation

#### Designing the new operation

#### Choosing which mock data response to get from Prism

#### Formalizing and suggesting the change

#### Extra curl examples

## 13 Building a backend with Node.js and Swagger Codegen

### 13.1 The problem

### 13.2 Introducing Swagger Codegen

#### Client code generation

#### Server code generation

#### Swagger Generator

### 13.3 The backend structure

#### Generating the backend

#### Investigating the structure

#### OpenAPI changes

### 13.4 Updating OpenAPI for the backend

#### dding operation IDs

#### agging API operations

#### egenerating the backend stubs

### 13.5 Running and testing the backend

#### Testing with Postman

#### Testing input validation

#### Output validation with Prism

### 13.6 Database persistence with Mongoose

#### Another API modification

#### Getting ready to use MongoDB

#### Configuring Mongoose in the project

#### Creating models

### 13.7 Implementing API methods

## 14 Integrating and releasing the web application

### 14.1 The problems

#### Authentication

#### Organizing code

#### Serving both components

### 14.2 Implementing authorization

#### Creating a security scheme

#### Adding a “Login” action

#### Defining operation security

### 14.3 Managing repositories

#### Keeping the existing structure

#### Creating a shared Git repository to implement both components

#### Combining code and API definition in a repository

#### Making the choice and refactoring

### 14.4 Setting up an integrated web server

#### RL design

#### erver setup

#### art 3 Extending APIs

## 15 Designing the next API iteration

### 15.1 Reviewing the first development sprint

### 15.2 Planning the next sprint

### 15.3 Preparing for new features

#### Reviewing the domain model

#### Reviewing user stories

### 15.4 Improving the developer experience

#### Consistency

#### Error handling

#### Input validation

#### Versioning vs. evolvability

## 16 Designing schemas with composition in OpenAPI

### 16.1 The problem

### 16.2 Polymorphism and inheritance in domain models

### 16.3 Updating the schemas

#### The Pet schema

#### The Dog schema

#### The Cat schema

### 16.4 Polymorphism and inheritance in OpenAPI

#### Composition inside the Dog and Cat schemas

#### Composition inside the Pet schema

### 16.5 Adding discriminators in OpenAPI

## 17 Scaling collection endpoints with filters and pagination

### 17.1 The problem

### 17.2 Designing filters

#### Projection filters

#### Selection filters

#### Handling nested schemas

#### Query languages

#### Special conventions

### 17.3 Filters for PetSitter

#### Finding filter fields

#### Adding filters to OpenAPI

#### Making a request

### 17.4 Designing pagination

#### Offset-based and page-based pagination

#### Cursor-based pagination

### 17.5 Pagination for PetSitter

#### Adding pagination to OpenAPI

#### Extending our request example

### 17.6 Designing sorting

#### Single-field sorting

#### Multifield sorting

#### Consistency throughout parameter types

#### 17.7 Sorting for PetSitter

#### Finding sorting fields

#### Designing the sort parameter

#### Adding sorting to OpenAPI

#### The final request example

## 18 Supporting the unhappy path: Error handling with problem+json

### 18.1 The problem

### 18.2 Error categories

#### Finding unhappy paths

#### Common error patterns

### 18.3 Requirements for error responses

### 18.4 The OAS tools format

### 18.5 The problem+json format

### 18.6 Adding error responses to OpenAPI

#### Creating error schemas

#### Adding errors to operations

### 18.7 Error-handling guidance

#### rontend development

#### ackend development

#### 9 Improving input validation with advanced JSON Schema

## 19.1 The problem

### 19.2 Supported validations

#### Read-only and write-only properties

#### Enforcing number constraints

#### Enforcing string formats

#### Enforcing array constraints

#### Defining enumerations

#### Listing required and optional properties

#### Setting defaults

### 19.3 Updating PetSitter schemas

#### User schema

#### Job schema

#### JobApplication schema

#### Pet, Dog, and Cat schemas

## 20 Versioning an API and handling breaking changes

### 20.1 The problem

### 20.2 What is a breaking change?

### 20.3 Releasing a breaking change

#### Coordinated breaking changes

#### Multiple API versions

#### Using media types to version operations

#### Adding and deprecating features

## 21 The API prerelease checklist

### 21.1 Pros and cons of a public API

### 21.2 The checklist

### 21.3 Getting the API working

#### Unit testing your API

#### End-to-end testing

### 21.4 Documentation

### 21.5 Getting your API consistent

### 21.6 Validation and error reporting

### 21.7 An API roadmap and exposure index

### 21.8 Getting a change strategy

### 21.9 Improving security

### 21.10 Monitoring your API

#### Setting up metric collection

### 21.11 Releasing the API

## appendix A Swagger 2.0, OpenAPI 3.0, and OpenAPI 3

index
