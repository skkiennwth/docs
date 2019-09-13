---
title: "Page Creation"
id: ""
sidebar_label: "Creating a Page"
---

When you create an app within WaveMaker, by default the Main Page is generated. In the process of app development, you will be adding pages and linking them as per the app workflow.

In this document, we will be seeing:

- how the [Main Page](#main-page) can be customized,
- [additional pages](#page-creation) can be created,
- different [types of pages](#page-types) available,
- different [page operations](#page-operations), and
- how information can be passed to the pages using [Page Parameters](#page-parameters).

The Main page comes with header, footer, top nav, left nav and right nav layout. This layout can be changed as per your needs ([more on layouts](/learn/app-development/ui-design/page-concepts/page-layouts/#page-layouts)). Wavemaker generates the HTML code which can be accessed from the markup tab.

Each element of the page layout - header, footer, topnav, leftnav and rightnav, which can be edited and customized. The change will be reflected in all pages using that element. Thus, giving a unified look and feel across multiple pages within the app. [![](/learn/assets/page_layout_edit.png)](/learn/assets/page_layout_edit.png)

## Page Creation - why and how

Pages are app components which allow you to organize data display by widget placement and help define the workflow. Following naming conventions have to be used when creating a page:

1. The page name should contain at least one character and it cannot be a number.
2. The page name should not contain special characters.
3. The page name should not start with a number.

New pages can be created to segregate the functionality of the app. Ideally, each page would cater to one business need of the app. New pages can use pre-built templates and layout. [![](/learn/assets/page_new.png)](/learn/assets/page_new.png)

## Types of Pages

There are two types of pages that can be created in an application:

1. **Page** – which can be loaded independently in the application. These act as a route within the application when associated with navigation events.
2. **Partial** - these have to be associated with a component within a page. Usually, a part of the page which is common across the app like a header or a left navigation, are implemented as a single partial and used across all app pages.

## Page Title

By default, WaveMaker provides the Main Page and any additional pages added are titled Page1, Page2 etc.. You can use the Page Title property to set the Page Title. [![](/learn/assets/page_title.png)](/learn/assets/page_title.png) You can use Page.pageTitle to change and access the page title. You can set the Page Title from Script tab using: Page.pageTitle = 'Profile'. Once set through Script any binding from the properties will be invalidated.

## Page Operations

You can duplicate, rename and delete a page using the page operations. These can be accessed from the more options against a given page or a partial page. [![page_operations](/learn/assets/page_operations.png)](/learn/assets/page_operations.png)

- **Renaming** a page or a partial page leads to the page name being renamed, with the new name given by you. All the references are also renamed.
- **Duplicating** a page leads to a copy of the page or partial page being created, with the new name given by you. A new goTo action for that page is also created.
- **Deleting** a page removes all references to the selected page from the project.

## Page Parameters

Data can be passed from one page to another within an app by defining **Page Params** for pages and partial pages. There are many scenarios where one needs to pass data to a particular page. For example:

- displaying the employee details working in a selected department,
- displaying profile for a specific user based upon some dynamic constraint, or
- loading a personalized page like for activation links etc..

### How parameters work

A typical page URL for a given app would be like this: https://www.app.com/#pagename Once the Page Param has been defined the URL changes to https://www.app.com/#pagename?param1=1&param2=abc This URL format will allow the data to be retained on browser refresh and reload. As is evident from the above example, multiple parameters are also supported.

### Steps to adding Page Params

There are two aspects to adding Page Params:

1. Parameterized Page: Page needing input to render the data on the page needs to _define_ page-level parameters to hold this input and _access_ the param value within the page
2. Page calling the above parameterized-page needs a way to _pass the value_ to the parameter

Let us say that test\_page needs an id to render the data and it has to be invoked from Main Page with the needed value for id.

1. Parameterised Page:
    - Add the parameter fields to the parameterized page (in this case, _test\_page_) by giving it a Name and specifying the Type. Currently, the supported types for page param are string, integer, boolean and date.⁣ [![](/learn/assets/pp_params.png)](/learn/assets/pp_params.png)
    - Page Params are available on the page/partial scope and can be used in the same. These parameters can be accessed from the Page Param tab on the binding dialog. [![](/learn/assets/pp_bind.png)](/learn/assets/pp_bind.png)
2. Calling Page:
    - The Application-scoped Navigation Action generated by default by WaveMaker for test\_page can be used to bind a value for the id field from the Main Page. The param will be available in the data tab of the Actions (goToPage\_test\_page). You can also create another Navigation Action and use it in a different navigation flow. [![](/learn/assets/pp_navvar.png)](/learn/assets/pp_navvar.png)

We have seen how a page can be added to WaveMaker app, it's title and layout set. We also saw how page parameters can be used to pass information to pages. Learn more about [Partial Pages](/learn/app-development/ui-design/page-concepts/partial-pages/), [Page Layouts](/learn/app-development/ui-design/page-concepts/page-layouts/), and [Page Templates](/learn/app-development/ui-design/page-concepts/page-templates/).
