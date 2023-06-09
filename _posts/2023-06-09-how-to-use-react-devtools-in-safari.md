---
layout: post
title: How to Use React DevTools in Safari
description: React DevTools are an excellent utility for debugging and tuning
  your react application, but so far there is no extension for Safari like there
  is for Chrome and Firefox.
categories: platforms
cta: Playbook
author: lucien
date: 2023-06-09T19:49:06.050Z
img: /assets/posts/how-to-use-react-devtools-on-safari.png
---
React is commonly used for the frontend in static site generators like [Gatsby](https://draft.dev/learn/creating-gatsby-starters) and now [WordPress](https://draft.dev/learn/getting-started-with-wordpress-development-a-developers-guide). [React DevTools](https://react.dev/learn/react-developer-tools) is a set of developer tools with a multitude of features that can make your workflow more efficient and help you debug and optimize your code.

However, if you use Safari, you may be disappointed to learn that there is no browser extension for React DevTools like there is in Chrome and Firefox.

Fortunately, there is a solution. You can still use standalone React DevTools to connect to your site in Safari. This practical tool is also useful for debugging non-browser-based React applications, like React Native apps. It can help simplify the process of optimizing and debugging your code, making your workflow more efficient.

In this article, you'll learn how to install and use the standalone version of React DevTools to debug a React application running in Safari. In addition, the article also highlights the differences between the standalone version and the Chrome extension, as well as some limitations of the tools.

## Use Cases for Debugging React Apps

The standalone version of React DevTools is a separate application that provides a powerful set of debugging and inspection tools for React applications. It's independent of any specific browser and can be used across various platforms and environments. This makes it a versatile option for developers who need to debug their React apps in different contexts.

Some of the use cases for the standalone version of React DevTools include:

- **Debugging non-browser-based React apps:** The standalone version of React DevTools is particularly useful when debugging React Native applications because it is platform-independent and can connect to apps running on iOS or Android devices. For example, you can use it to determine why a specific component of your React Native app isn't rendering correctly on an iOS device. You can use React DevTools to inspect the component tree, check component props and state, and identify issues with styling or logic that may be causing the rendering problem.
- **Debugging React apps in Safari:** Safari is a widely used browser, especially among macOS users. Although Safari has its own set of developer tools, it doesn't have extensions or support for React applications like Chrome or Firefox. The standalone version of React DevTools can be used to debug React applications running in Safari, as it provides developers with a powerful set of tools to inspect components and diagnose issues. For instance, if a specific UI component in your React app doesn't behave as expected when viewed in Safari, you can use React DevTools to inspect the component in question. You can check its state and props and identify any issues.
- **Debugging server-rendered React apps:** In most static site generators, React apps are server-rendered, which means components are rendered on the server side and sent as HTML to the client. In these scenarios, the standalone version of React DevTools can help you debug issues related to server-rendered components. For example, if you're using a solution like [Next.js](https://nextjs.org/) or [React Server Components](https://nextjs.org/docs/advanced-features/react-18/server-components) to perform server-side rendering, you can use the standalone version of React DevTools to inspect the rendered components and identify issues related to data fetching, state management, or rendering logic.

## How to Debug a React App in Safari

The following tutorial explains how to use the standalone version of React DevTools to debug a React application running in Safari. By the end, you'll be equipped with the knowledge and tools you need to confidently debug your React application.

### Prerequisites

To complete this tutorial, you'll need:

- A Mac running [Safari](https://support.apple.com/downloads/safari)
- A code editor, such as [Visual Studio Code](https://code.visualstudio.com)
- [Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git) installed on your machine
- [Node.js](https://nodejs.org/) and [npm](https://www.npmjs.com/) (the Node package manager) installed on your system

To verify the installation of Node.js and npm, execute these commands in your shell or terminal:

```shell
node --version
npm --version
```

If they aren't installed, [download and install Node.js](https://nodejs.org/en/download), which also automatically installs npm. This tutorial uses Node version 18.12.1 and npm version 8.19.2.

### Creating a React Demo Application

You'll first need to set up a basic React demo application, which you'll run and debug in your Safari browser using the standalone version of React DevTools.

Create a new React project using [Create React App](https://create-react-app.dev/) by executing this command:

```shell
npx create-react-app react-sample-app
```

This command will generate a new folder with the specified name and populate it with boilerplate code for a React application.

Change the current directory to your newly created project folder by running the following command:

```shell
cd react-sample-app
```

Execute the following command to start the development server:

```shell
npm start
```

Your React application should now be live at [http://localhost:3000/](http://localhost:3000/). Use your Safari browser to open the application:

![React demo application in Safari](https://i.imgur.com/HqgadpR.png)

Any modifications made to the source code will trigger an automatic page refresh.

### Connecting Standalone React DevTools to Your App in Safari

To connect React DevTools to your app in Safari, you first need to install the [standalone React DevTools package](https://www.npmjs.com/package/react-devtools) using npm from your terminal or shell:

```shell
npm install -g react-devtools@^4 
```

Run React DevTools with this command:

```shell
react-devtools
```

After you run the command, you'll get the following screen telling you to add an additional script to your [React DOM](https://react.dev/reference/react-dom):

![React DevTools prompt](https://i.imgur.com/tzLtNyU.png)

This tutorial uses the script with the localhost link (`<script src="http://localhost:8097"></script>`) to connect the React application, but the LAN IP address also works. Since you're not working with a mobile application, the localhost link will work just fine.

Go to your source project and open the `index.html` file in the `public` folder. Add the localhost link just after the `<head>` tag, then open React DevTools. You should see the following in the Components section:

![Debugging with standalone React DevTools](https://i.imgur.com/oqtb6XR.png)

### Creating a User Listing

Once you have connected React DevTools to your application, you can use the various features it provides. These features include the ability to inspect the component tree, examine component state and props, and profile component performance.

As the sample application doesn't have many components, you'll only see the `App` component in the tree. To explore more features of React DevTools, you'll need to add more components.

To add a `User` component, create a file named `User.js` in the `src` folder and add the following code to it:

```javascript
import React from 'react';
const User = ({ user }) => {
  return (
    <div className="user">
      <p>First Name: {user.firstname}</p>
      <p>Last Name: {user.lastname}</p>
      <p>Age: {user.age}</p>
      <p>DOB: {user.dob}</p>
    </div>
  );
};
export default User;
```

This component displays user information, such as first name, last name, age, and date of birth (DOB).

You'll now create a `UsersList` component that utilizes the `User` component to display the list of users. Create a file named `UsersList.js` in the `src` folder and add the following code to it:

```javascript
import React from 'react';
import User from './User';

const UsersList = ({ users }) => {
  return (
    <div className="users-list">
      {users.map((user) => (
        <User key={user.id} user={user} />
      ))}
    </div>
  );
};

export default UsersList;
```

To populate the list of users, you need to create some dummy data and wrap the `UsersList` component in the `App` component. To do this, replace the code in `App.js` with the following:

```javascript
import React from 'react';
import UsersList from './UsersList';

const App = () => {
  const users = [
    { id: 1, firstname: 'John', lastname: 'Doe', age: 30, dob: '1993-02-15' },
    { id: 2, firstname: 'Jane', lastname: 'Doe', age: 28, dob: '1995-06-20' },
    { id: 3, firstname: 'Mark', lastname: 'Smith', age: 35, dob: '1988-10-05' },
  ];

  return (
    <div className="App">
      <h1>Users List</h1>
      <UsersList users={users} />
    </div>
  );
};

export default App;
```

**Note:** The `App` component renders the `UsersList` component, which in turn renders each `User` component for every user in the list.

The application in your Safari browser should look like the following:

![React users list in Safari browser](https://i.imgur.com/CNEmrnO.png)

### Debugging and Inspecting Your App

Now that your application is ready, you can start debugging it with React DevTools.

If you open React DevTools, you should see your application tree. It begins with the `App` component at the top, followed by the `UsersList` component, and ends with the `User` component:

![Application tree](https://i.imgur.com/zTLN8d2.png)

If you click the `UsersList` component in the tree, the props that are passed to the component will be displayed in the right pane. In this case, the props include the array of `users` from your dummy data:

![UsersList component](https://i.imgur.com/9gP4Qgw.png)

Clicking a `User` component displays the props that it passes (the `user` object in this case). You can click any of three `User` components and check their relative props:

![User component](https://i.imgur.com/YmPMtGC.png)

When you use React DevTools to debug your application, it's important to understand the application tree and how it represents the component hierarchy. The application tree can help you quickly identify rendering issues and data flow by providing a visual representation of the components. You can inspect the props and state of each component to pinpoint bugs and troubleshoot issues that may arise.

Additionally, you can pin the location of a selected component in your browser by clicking the eye icon in React DevTools:

![Pinning a component in React DevTools](https://i.imgur.com/LDJYZhW.png)

Once this has been activated, it will highlight the component in light blue in your browser:

![Selected component in the browser](https://i.imgur.com/IpuC0rW.png)

You can also log the selected component in the console by clicking the bug icon in React DevTools:

![Logging a component in React DevTools](https://i.imgur.com/he5JxeL.png)

The following image shows the results in the browser when you click the bug icon:

![Logging a component in the browser](https://i.imgur.com/TblI90n.png)

Using React DevTools, you can gain a better understanding of the structure and behavior of your applications. You can also more easily identify and fix bugs and performance issues. The standalone version is particularly useful because it can be used with any React application, whether it's running locally or on a remote server, and it provides a separate, dedicated window for debugging purposes. Overall, the standalone version of React DevTools is a practical tool for developing and debugging React applications.

## Differences between Standalone React DevTools and the Chrome Extension

If you use the standalone version of React DevTools, you'll be able to use it with any browser, not just Safari. It also offers more customization options and flexibility compared to the Chrome extension. The following are some other differences between the two versions:

- **Cross-platform compatibility:** The standalone version of React DevTools is designed to work across various platforms, including browsers and devices, enabling a broader range of debugging and development possibilities. Chrome extensions, on the other hand, are limited to working within the Chrome browser environment.
- **Ease of setup and connection:** Chrome extensions are designed to integrate seamlessly with the browser, so using the extension version makes it easy to detect and connect to React apps running in the browser. The standalone version of React DevTools often requires manual configuration to connect to the target app, which can be more time-consuming and error-prone.
- **Updates and maintenance:** These two versions of React DevTools may have different release schedules and update processes. Chrome extensions typically update automatically with the browser, while the standalone version may require manual updates.

## Limitations of Standalone React DevTools

It's also important to be aware that the standalone version of React DevTools has some limitations. For instance, the tool may not work as effectively with certain types of components, such as those built with third-party libraries. You may need to use additional tools or methods to gather the necessary information if the tool provides limited data.

The following are some of the most notable limitations:

- **Browser-specific features:** The standalone version of React DevTools may lack some browser-specific features, such as network request inspection, JavaScript debugging, or browser performance profiling. For these features, developers need to use the browser's built-in developer tools or rely on other debugging solutions tailored for the specific browser.
- **Integration with browser environment:** The standalone version doesn't have the same level of integration with the browser environment as the extensions. Certain tasks, like interacting with browser APIs or manipulating the DOM, may be more challenging or impossible to accomplish using the standalone version.
- **Learning curve:** Due to differences in features, interface, and setup process, developers may need to invest additional time in learning how to use the standalone version of React DevTools. This may slow down their development process, especially if they are already familiar with the Chrome extension.
- **Performance and resource usage:** The standalone version of React DevTools may have different performance characteristics and resource usage compared to the Chrome extension version. Depending on the specific tools and configurations used, developers may experience varying levels of performance and resource consumption, which can impact their development experience.

By keeping these limitations in mind, you can adjust your approach and optimize your code more effectively. For instance, you can use alternative tools or workarounds to gather the information you need.

## Conclusion

The standalone version of React DevTools offers a versatile solution for developers who need a powerful and flexible set of debugging tools, whether they're working on browser-based React apps or non-browser-based applications like React Native apps. 

This article introduced the standalone version of React DevTools and demonstrated how to use it to debug a React app running in Safari. You should now be comfortable with setting up, connecting, and using React DevTools to inspect and debug your React applications. With the knowledge from this article, you'll be able to debug your React applications, regardless of the environment or browser they are running in.

You can find the code that was used in this article in [this GitHub repository](https://github.com/See4Devs/react-sample-userslist-app).
