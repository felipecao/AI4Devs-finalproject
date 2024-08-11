> Detalla en esta sección los prompts principales utilizados durante la creación del proyecto, que justifiquen el uso de asistentes de código en todas las fases del ciclo de vida del desarrollo. Esperamos un máximo de 3 por sección, principalmente los de creación inicial o los de corrección o adición de funcionalidades que consideres más relevantes.

Puedes añadir adicionalmente la conversación completa como link o archivo adjunto si así lo consideras


## Índice

1. [Descripción general del producto](#1-descripción-general-del-producto)
2. [Arquitectura del sistema](#2-arquitectura-del-sistema)
3. [Modelo de datos](#3-modelo-de-datos)
4. [Especificación de la API](#4-especificación-de-la-api)
5. [Historias de usuario](#5-historias-de-usuario)
6. [Tickets de trabajo](#6-tickets-de-trabajo)
7. [Pull requests](#7-pull-requests)

---

## 1. Descripción general del producto

**Prompt 1:**

i'm developing a product that is meant to make it much easier working with invoices. what the product does is offering a page where you can upload invoices in PDF format, and later you can ask questions about the invoices, such as:
- how much have i spent in the last 30 days?
- how many invoices coming from company ABC have been uploaded?
- how much money is due to company ABC?

please generate 5 possible names for my product

**Prompt 2:**

great, i'll go with Invoicelytics. Now I want to have a brief description of the product. It should make its purpose clear, the value it adds, what kind of problems does it solve and for whom.

**Prompt 3:**

---

## 2. Arquitectura del Sistema

### **2.1. Diagrama de arquitectura:**

**Prompt 1:**

please generate an architecture diagram for a system called Invoicelytics.

As this is an alpha product at a very early stage, i want to keep its architecture very lightweight and simple.

it's composed of the following elements:
- a postgres database deployed at Aiven.io
- a Python monolith deployed at render.com, containing both the backend and frontend code
- an AI model pulled from huggingface that's used by the Python monolith

Please make sure to provide a user icon and to make sure the Python monolith and the AI model are represented within a box, indicating they're deployed on render.com.

**Prompt 2:**

**Prompt 3:**

### **2.2. Descripción de componentes principales:**

**Prompt 1:**

now let's talk about the architecture of the solution. here's a description of the architecture, complemented by the attached architecture diagram.

```
Invoicelytics is a very early-stage product, with a very small team, composed of 1 person (myself), and I come from a backend engineering background.

As the product is still at a very insipient stage, the architecture focuses on simplicity. It's composed of 3 very basic elements:
- a monolith written in Python, which is the language I'm most proficient with among the allowed languages, and deployed for free on render.com
- a Postgres instance deployed on Aiven.io, a free Postgres service
- an AI model to enable user questions in natural language about the invoices uploaded into the platform

The main benefits of this architecture are as follows:
- **Low costs**: most cloud providers are free
- **Focuses on strengths**: with a strong backend engineering background, having a SPA would require investing significat amounts ot time and energy to have a codebase in a optimal state, which would be likely to extrapolate the amount of time available for this task. Instead, this architecture focuses on technologies I'm proficient with and that also intersect with what I use on daily work
- **Simple and easy to pivot**: a simple architecture focused on things I'm used to makes me more agile, enabling me to pivot if necessary and turn the product in a different direction.
```

Based on this description and the attached diagram, please provide a brief description of the components, including the technology used in each of them.

**Prompt 2:**

**Prompt 3:**

### **2.3. Descripción de alto nivel del proyecto y estructura de ficheros**

**Prompt 1:**

**Prompt 2:**

**Prompt 3:**

### **2.4. Infraestructura y despliegue**

**Prompt 1:**

**Prompt 2:**

**Prompt 3:**

### **2.5. Seguridad**

**Prompt 1:**

please list up to 5 security practices you'd suggest implementing for this system. please take into consideration this is supposed to be an Minimum Viable Product and that its current state is very early stage and insipient.

**Prompt 2:**

**Prompt 3:**

### **2.6. Tests**

**Prompt 1:**

please describe up to 5 tests that should be performed on Invoicelytics. please focus on the following main features:

1. **Automated Invoice Upload and Processing**: Users can easily upload invoices in PDF format, and Invoicelytics automatically extracts and organizes the relevant data, eliminating the need for manual entry and reducing the risk of errors.

1. **Vendor Management and Tracking**: Invoicelytics enables users to manage and track invoices by vendor, making it easy to see how much money is due, which invoices have been paid, and which are still outstanding. This feature helps users maintain healthy vendor relationships and avoid missed payments.

1. **AI-Powered Chat Assistance**: Invoicelytics features an intelligent chat assistant that allows users to ask questions about their invoices using natural language. Whether you want to know your total expenses for the month, the number of invoices from a specific vendor, or outstanding payments, the AI assistant provides instant, accurate responses, making invoice management effortless.

**Prompt 2:**

**Prompt 3:**

---

### 3. Modelo de Datos

**Prompt 1:**

now i want to identify the main database tables that will be required to support the use cases identified so far.

the following restrictions should be taken into consideration:
1. Invoicelytics should extract at very least the following information from an invoice:
- payee: what's the name of the company receiving the amount contained in the invoice
- payee address: the address of said company
- invoice number: a number or code that identifies the invoice
- issued date: the date in which the invoice was issued
- total amount: the total amount of the invoice
- tax amount: the amount of tax due on that invoice
- due date: when the invoice is due

2. the system is supposed to be multi-tenant, ie, an Invoicelytics user is bound to an account (aka tenant) and each invoice should be bound to the respective tenant

3. we should track which user uploaded the invoice and which user validated that the data extraction was correct

don't generate any code or SQL DDL right now. please ask for any clarifications and wait for my approval before proceeding. please feel free to suggest other tables and columns, apart from what i've defined above.

**Prompt 2:**

let's refine your initial proposal with other considerations:
- i don't want a vendors table for now
- i don't want an Invoice_Items table
- the invoice should have a status column. allowed values are: created, processed, validated.
- let's remove the Invoice_Files table as well. i'm happy with just having a `pdf_file_path` column at invoices.

now please generate a model-entity relationship diagram based on the definitions we've discussed. use mermaid syntax. the names of the tables should be lower case, as well as columns name. be sure to include respective data types for each column, considering that the database engine to be used is postgres.

please generate another proposal based on the answers above.

**Prompt 3:**

can you also add information about nullability constraints, as well as unique constraints? please consider that everything in invoices table is nullable (except for its primary key). please use markdown for that.

---

### 4. Especificación de la API

**Prompt 1:**

now consider that the frontend and backend components of Invoicelytics will talk to each via a RESTful API. please suggest up to 5 endpoints the application should have.

**Prompt 2:**

let's focus on suggestions #3, 4 & 5. please give me their explanations in a markdown block. be sure to not change the suggestions you just gave me for each of them.

**Prompt 3:**

---

### 5. Historias de Usuario

**Prompt 1:**

now let's talk about organizing work. please put together up to 5 users stories that deliver the features we've previously discussed.

please the following format when describing a user story:
- [SHORT SUMMARY]: As a [USER], I want to [FEATURE], so that [VALUE ADDED BY THAT STORY TO THE USER

Along with each user story, provide up to 3 acceptance criteria. The acceptance criteria should be described using bullet points and be very concise.

**Prompt 2:**

let's focus on stories 2, 4 & 5. please include acceptance criteria to each story ensuring that users should not be able to see data that belongs to a different tenant. use markdown format.

**Prompt 3:**

---

### 6. Tickets de Trabajo

**Prompt 1:**

i want to split the user story Upload Invoice into multiple tickets. how would you propose splitting it, considering the need to implement different types of code: SQL, backend code, frontend code, etc?

**Prompt 2:**

**Prompt 3:**

---

### 7. Pull Requests

**Prompt 1:**

**Prompt 2:**

**Prompt 3:**
