### **React Basics**

1. Introduction to React
      React is an open-source JavaScript library developed by Facebook for building user interfaces, specifically single- page applications. React was first released on March 2013. It emphasizes component-based architecture, allowing developers to build encapsulated components that manage their state. Unlike traditional MVC frameworks like Angular, React focuses solely on the "View" aspect of MVC, making it lightweight and faster. React also introduces the concept of a virtual DOM, which optimizes the performance of UI rendering by reducing the number of direct manipulations to the actual DOM.
      
      The features of React are as follows:
      
      1. **JSX:**
      JSX serves as a syntax extension to JavaScript, facilitating the combination of HTML structures with JavaScript code within React files.
          - Explain JSX
              
              JSX (JavaScript XML) is a syntax extension for JavaScript recommended by React for describing what the UI should look like.
              
              JSX (JavaScript XML) is a syntax extension for JavaScript that resembles HTML. It is used in React to describe what the UI should look like. JSX makes the code more readable and easier to write by allowing developers to use HTML-like syntax directly within JavaScript. Under the hood, JSX is transformed into regular JavaScript function calls (e.g., React.createElement) that construct React elements. This enables the declarative style of programming in React, where the UI is described as a function of the application's state.
              
          - How can a browser read JSX file?
              
              If you want the browser to read JSX, then that JSX file should be replaced using a JSX
              transformer like Babel and then send back to the browser.
              
          - Does React use HTML?
              
              No, It uses JSX, which is similar to HTML.
              
      2. **Components:**
          - Notes
              
              The features of React are as follows:
              
              **Element**
              
              An Element is a simple object that describes what you want to show on the screen. It defines the structure of DOM nodes or other components. Elements can include other Elements in their properties. Once created, Elements cannot be changed. Creating a React Element is a straightforward and inexpensive operation.
              
              **Example of creating an Element using JSX:**
              
              JSX serves *as* a syntax extension to JavaScript, facilitating the combination of HTML structures with JavaScript code within React files.
              
              ```jsx
              **// JSX
              const** element **=** <div **id**="**login**-btn"**>Login</div>**;
              ```
              
              **When expressed without JSX**, **it would look like:**
              
              ```jsx
              // JSX
              const element = React.createElement("div", { id: "login-btn" }, "Login");
              ```
              
              **This element is essentially an object:**
              
              ```jsx
              {
                type: 'div',
                props: {
                  children: 'Login',
                  id: 'login-btn'
                }
              }
              ```
              
              This object is then rendered to the DOM using ReactDOM.render().
              
              ```jsx
              // JSX
              const **element** = **React.createElement(**"div", { **id**: **"login**-btn" }, "Login"**)**;
              ```
              
              **Component**
              
              A Component can be declared in various ways. It can be a class with a render() method, or it can be defined as a function. Components take props as input and return a JSX tree as output. Components are more powerful and flexible compared to Elements.
              
              **Example of creating a functional Component using JSX**
              
              ```jsx
              // JSX
              
              const Button = ({ handleLogin }) => (
                <div id="login-btn" onClick={handleLogin}>
                  Login
                </div>
              );
              ```
              
              **When transpiled, it becomes**:
              
              ```jsx
              // JSX
              
              const Button = ({ handleLogin }) =>
                React.createElement(
                  "div",
                  { id: "login-btn", onClick: handleLogin },
                  "Login"
                );
              ```
              
              In this example, Button is a functional component that takes handleLogin as a prop and returns a JSX tree. Components are a more dynamic way to create reusable pieces of UI.
              
              Components are the fundamental building blocks of a React application. They are reusable, self-contained pieces of UI that can manage their state and interact with other components via props. Components can be either class-based or functional. They allow for better organization, maintainability, and scalability of large applications by breaking down the UI into smaller, manageable parts. Each component can be independently developed, tested, and reused across different parts of an application or even across different projects.
              
              1. **Virtual DOM:**
              React employs a Virtual DOM, which is a lightweight representation of the actual DOM stored in memory. This approach allows React to selectively update only the relevant parts of the real DOM when the state of an object changes.
                  - State the difference between Real DOM and Virtual DOM
                      
                      The virtual DOM is a lightweight copy of the actual DOM in memory. React uses it to improve performance by updating only the changed parts of the actual DOM.
                      
                      | Real DOM | Virtual DOM |
                      | --- | --- |
                      | It is updated slowly. | It updates faster. |
                      | It allows a direct update from HTML. | It cannot be used to update HTML directly. |
                      | It wastes too much memory. | Memory consumption is less |
                      
                      Virtual DOM is a lightweight representation of the real DOM. It is a JavaScript object that describes the current state of the UI. When the state of the UI changes, React updates the Virtual DOM. Then, React compares the Virtual DOM to the real DOM and efficiently updates the real DOM only with the changes that are needed.
                      
                      ---
                      
                      The Virtual DOM is like a blueprint or a copy of the real DOM that is stored in the computer's memory. It's a concept used by React to make updating and changing things on a webpage more efficient.
                      
                      ![Screenshot 2025-07-13 at 4.58.50 PM.png](/images/Screenshot%202025-07-13%20at%204.58.50 PM.png)
                      
                      **Why is it Needed?**
                      
                      When we make changes to a webpage, like updating a list, traditional methods often involve updating the entire webpage, even if only a small part has changed. This can be slow and inefficient.
                      
                      How does the Virtual DOM work??
                      
                      Virtual DOM is a JavaScript object that describes the current state of the UI. It is a tree structure, with each node in the tree representing an element in the UI. The Virtual DOM also includes information about the attributes and children of each element. To update the real DOM, React uses a process called reconciliation. Reconciliation compares the Virtual DOM to the real DOM and determines the minimal set of changes needed to bring them into alignment. React then applies these changes to the real DOM. Reconciliation is a very efficient process. React uses a diffing algorithm to compare the Virtual DOM to the real DOM. This algorithm is able to identify the smallest possible set of changes needed to update the real DOM.
                      
                      ![Screenshot 2025-07-13 at 5.02.21 PM.png](attachment:67ee3585-eeee-44f9-9487-85f1647400c4:Screenshot_2025-07-13_at_5.02.21_PM.png)
                      
                      1. **Virtual DOM Objects:** For every object on the webpage, there is a corresponding virtual object in the memory. These virtual objects have the same properties as the real objects.
                      2. **Blueprint of the DOM:** Think of the virtual DOM as a blueprint of the real DOM. Changes made to the virtual DOM don't immediately show up on the screen; they are like plans for what should change.
                      3. **Faster Updates:** Updating the virtual DOM is much faster than updating the real DOM. It's like working on a draft before finalising a document.
                      4. **Two Virtual DOMs:** React uses two sets of virtual DOMS - one to store the current state and another to store the previous state of objects.
                      5. **Efficient Updating:** When something changes, React compares the two virtual DOMS to see what's different. It then updates only the parts that have changed in the real DOM, rather than updating the entire webpage.
                      
                      In simpler terms, the Virtual DOM is like a behind-the-scenes helper that makes updating web pages faster and more efficient by smartly figuring out what needs to change and updating only those parts.
                      
                  - Explain the term reconciliation
                      
                      When a component's state or props change then rest will compare the rendered element with previously rendered DOM and will update the actual DOM if it is needed. This process is known as reconciliation.
                      
              2. **Data Binding:**
              React adopts a one-way data-binding approach, ensuring a modular and efficient structure. Unidirectional data flow signifies that in a React app, child components are often nested within parent components.
              3. **High Performance:**
              React's high performance is driven by its ability to update only the components that undergo changes, rather than refreshing the entire set. This results in significantly faster web applications.
              
              'create-react-app' is a command-line tool which allows you to create one basic react application.
              
              ---
              
              **Steps to Create a React Application**
              
              1. **Install Node:** Before installing React, ensure that Node is installed on your computer. You can download it from `Node.js` official site.
              2. **Create React App:** Open the terminal and run the following command to create a new React application (replace `my-react-app` with your preferred application name):
              
              ```jsx
              // JSX
              npx create-react-app my-react-app
              ```
              
              Navigate to the Application Folder: Move to the newly created application folder:
              
              ```jsx
              // JSX
              cd my-react-app
              ```
              
              **Print "Hello World!" Example:** Now, open the **src**/App.js file and replace its content with the following:
              
              ```jsx
              // JSX
              
              import React from 'react';
              
              export default function App() {
                return (
                  <div>
                    <h1>Hello World!</h1>
                  </div>
                );
              }
              
              // Save the file.
              ```
              
              **Run the Application:** In the terminal, run the following command to start the development server:
              
              ```jsx
              // JSX
              npm start
              ```
              
              This will open your new React application in a web browser, and you should see "Hello World!" displayed on the webpage.
              
              In this example, the `App` component is a simple React function component that returns JSX to render the "Hello World!" message. The `npm start` command is used to run the application and launch a development server.
              
              The React Developer Tools is a browser extension that allows developers to inspect and debug React component hierarchies in the Chrome and Firefox browsers.
                
        - Explain strict mode
            
            StrictMode allows you to run checks and warnings for react components. It runs only on
            development build. It helps you to highlight the issues without rendering any visible UI.
            
            ---
            
            `React.StrictMode` is a component designed to highlight potential issues and enforce best practices in a React application. It does not introduce additional DOM elements and operates exclusively in development mode.
            
            **Usage**
            
            Wrap parts of the application in `<React. StrictMode>` to activate additional checks and warnings.
            
            **Development Mode Only**
            
            Strict mode checks apply exclusively in development mode, helping developers catch potential problems early.
            
            **Example**
            
            In the example below, strict mode checks apply to `<ComponentOne>` and `<Component **Two>**`.
            
            ```jsx
            import React from "react";
            
            function ExampleApplication() {
            	return (
            		<div>
            			<Header />
            			<React.StrictMode>
            			<div>
            				<ComponentOne />
            				<Component Two />
            			</div>
            			</React.StrictMode>
            			<Header />
            		</div>
            	);
            }
            ```
            
            **Strict Mode Checks**
            
            - Identifies components with unsafe lifecycle methods.
            - Warns about the usage of legacy string refs.
            - Warns against using findDOMNode method.
            - Highlights potential issues with legacy context API usage.
        - How are comments written in React?
            
            Comments in React/JSX are similar to JavaScript multiline comments but are enclosed in curly braces.
            
            **Single-line comments**
            
            ```jsx
            // JSX
            
            <div>
            	{/* Single-line comments(In vanilla JavaScript, 
            			the single-line comments are represented by double slash(//)) */}
            	{`Welcome, ${userName}! Let's dive into React`}
            </div>
            ```
            
            **Multi-line comments**
            
            ```jsx
            // JSX
            
            <div>
            	{/* This is a multiline comment in React.
            			It provides additional information about the code. */}
            	{`Welcome, ${userName}! Let's dive into React`}
            </div>
            ```
            
            In these modified examples, the comments now convey a welcoming message to the user, demonstrating how comments can be used to explain and document code within the JSX structure.
            
        - Give me two most significant drawbacks of React
            1. Integrating React with the MVC framework like Rails requires complex configuration.
            2. React require the users to have knowledge about the integration of user interface into MVC framework.
        - Name the important features of React
            
            Here, are important features of React.
            
            1. Allows you to use 3rd party libraries.
            2. Time-Saving
            3. Faster Development
            4. Simplicity and Composable
            5. Fully supported by
            6. Facebook.
            7. Code Stability with One-directional data binding React Components
            
            React is a popular JavaScript library for building user interfaces, and it offers a variety of features that make it a powerful tool for web development. Here are some of the key features of React:
            
            1. **Component-Based:** React is built around the concept of reusable UI components, making it easy to manage and maintain code.
            2. **Virtual DOM:** React's virtual DOM efficiently updates the actual DOM, improving rendering performance. 
            3. **JSX:** JSX allows developers to write HTML-like code within JavaScript for defining component structures.
            4. **Unidirectional Data Flow:** Data flows in one direction, simplifying data management and updates.
            5. **Reusability:** React components can be reused across the application, promoting code reusability.
            6. **Declarative:** React allows you to describe what your UI should look like, and it takes care of updating the DOM accordingly.
            7. **Community and Ecosystem:** React has a large and active developer community and a rich ecosystem of libraries and tools.
            8. **Performance Optimization:** React provides tools for optimizing performance, such as code splitting.
            9. **Support for Server-Side Rendering (SSR):** React can render on the server side, improving SEO and initial load times.
            10. **Developer Tools:** React offers browser extensions and tools for debugging and inspecting components.
        - Explain the term stateless components
            
            Stateless components are pure functions that render DOM based solely on the properties provided to them.
            
        - What is the one-way data flow in React?
            
            One-way data flow in React is a design pattern that ensures that data flows in one direction, from parent to child components.
            This helps to make React applications more predictable and easier to debug.
            
        - What is meant by callback function? What is its purpose?
            
            A callback function should be called when setState has finished, and the component is
            retendered. As the setState is asynchronous, which is why it takes in a second callback
            function.
            
        - Explain the Presentational segment
            
            A presentational part is a segment which allows you to renders HTML. The segment’s
            capacity is presentational in markup.
