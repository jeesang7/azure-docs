---
title: JavaScript single-page app scenario
description: Learn how to build a single-page application (scenario overview) by using the Microsoft identity platform.
services: active-directory
author: mmacy
manager: CelesteDG

ms.service: active-directory
ms.subservice: develop
ms.topic: conceptual
ms.workload: identity
ms.date: 10/12/2021
ms.author: marsma
ms.custom: aaddev, identityplatformtop40, devx-track-js
#Customer intent: As an application developer, I want to know how to write a single-page application by using the Microsoft identity platform.
---

# Scenario: Single-page application

Learn all you need to build a single-page application (SPA). For instructions regarding Azure Static Web Apps, see [Authentication and Authorization for Static Web Apps](../../static-web-apps/authentication-authorization.md) instead.

## Getting started

If you haven't already,  create your first app by completing the JavaScript SPA quickstart:

[Quickstart: Single-page application](./quickstart-v2-javascript-auth-code.md)

## Overview

Many modern web applications are built as client-side single-page applications. Developers write them by using JavaScript or a SPA framework such as Angular, Vue, and React. These applications run on a web browser and have different authentication characteristics than traditional server-side web applications.

The Microsoft identity platform provides **two** options to enable single-page applications to sign in users and get tokens to access back-end services or web APIs:

- [OAuth 2.0 Authorization code flow (with PKCE)](./v2-oauth2-auth-code-flow.md). The authorization code flow allows the application to exchange an authorization code for **ID** tokens to represent the authenticated user and **Access** tokens needed to call protected APIs. 

    Proof Key for Code Exchange, or _PKCE_, is an extension to the authorization code flow to prevent authorization code injection attacks. This IETF standard mitigates the threat of having an authorization code intercepted and enables secure OAuth exchange from public clients as documented in [RFC 7636](https://datatracker.ietf.org/doc/html/rfc7636). In addition, it returns **refresh** tokens that provide long-term access to resources on behalf of users without requiring interaction from those users. 

    Using the authorization code flow with PKCE is the more secure and **recommended** authorization approach, not only in native and browser-based JavaScript apps, but for every other type of OAuth client.

![Single-page applications-auth](./media/scenarios/spa-app-auth.svg)

- [OAuth 2.0 implicit flow](./v2-oauth2-implicit-grant-flow.md). The implicit grant flow allows the application to get **ID** and **Access** tokens. Unlike the authorization code flow, implicit grant flow does not return a **Refresh token**.

![Single-page applications-implicit](./media/scenarios/spa-app.svg)

This authentication flow does not include application scenarios that use cross-platform JavaScript frameworks such as Electron and React-Native. They require further capabilities for interaction with the native platforms.

## Specifics

To enable this scenario for your application, you need:

* Application registration with Azure Active Directory (Azure AD). The registration steps differ between the implicit grant flow and authorization code flow.
* Application configuration with the registered application properties, such as the application ID.
* Using Microsoft Authentication Library for JavaScript (MSAL.js) to do the authentication flow to sign in and acquire tokens.

## Recommended reading

[!INCLUDE [recommended-topics](../../../includes/active-directory-develop-scenarios-prerequisites.md)]

## Next steps

Move on to the next article in this scenario, [App registration](scenario-spa-app-registration.md).
