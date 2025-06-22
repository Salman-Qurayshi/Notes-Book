# Jira with Python - Python Flask - Vagrant - Ansible

> Created by Salman Al Qureshi
Linkedin: Salman Qureshi
> 
> 
> http://www.linkedin.com/in/salman-qureshi-4aa41a247
> 

# Jira With Python

 

- **Overview**
    
    ### Key Concepts
    
    - **Jira**: A project management tool used for tracking issues and managing projects. It includes features for issue tracking, project management, and agile development.
    - **Jira API**: Allows you to interact with Jira programmatically. You can perform actions like creating, updating, and querying issues.
    - **Authentication**: You'll need credentials (such as an API token) to authenticate and access the Jira API.
    You can get the api from:
     Setting —> Atlassian account settings —> Security —> Create and manage API tokens —>Create API Token
    - **Python Libraries**: Libraries like `jira` or `requests` can be used to interact with Jira through Python.
    
    **Basic Syntax and Example**
    
    - **Installing the Jira Library**: Use the command `pip install jira` to install the library.
    - **Connecting to Jira**: Import the `jira` library and create a connection using your Jira domain and API token:
        
        ```python
        from jira import JIRA
        jira = JIRA(server='https://your-domain.atlassian.net', basic_auth=('your-email', 'your-api-token'))
        
        ```
        
    - **Creating an Issue**: Define a dictionary with issue details like project key, summary, description, and issue type, then create the issue:
        
        ```python
        issue_dict = {
            'project': {'key': 'PROJ'},
            'summary': 'New issue from Python',
            'description': 'Creating an issue using Python script',
            'issuetype': {'name': 'Task'},
        }
        new_issue = jira.create_issue(fields=issue_dict)
        
        ```
        
    - **Querying Issues**: Use a JQL (Jira Query Language) query to fetch issues and print their details:
        
        ```python
        issues = jira.search_issues('project=PROJ AND status="To Do"')
        for issue in issues:
            print(issue.key, issue.fields.summary)
        
        ```
        
    - **Updating an Issue**: Retrieve an issue and update its fields:
        
        ```python
        issue = jira.issue('PROJ-1')
        issue.update(fields={'summary': 'Updated summary'})
        
        ```
        

- **Agile Principles**
    
    Agile is a mindset or approach focused on delivering value incrementally, responding to change, and promoting collaboration among teams. The following are key principles of Agile:
    
    1. **Iterative Development**:
        - Agile promotes iterative development, which means breaking the project into smaller chunks called iterations or sprints. Each iteration involves planning, executing, testing, and delivering a small part of the project, which adds up to the final product.
        - **Benefit**: This approach allows for continuous improvement, adjustments, and feedback after each iteration.
    2. **Adaptive to Changing Requirements**:
        - Agile methodologies are designed to be flexible and accommodate changes, even late in the development process. Requirements can evolve as customer needs or market conditions change.
        - **Benefit**: This helps ensure that the final product meets current demands and remains relevant.
    3. **Frequent Delivery**:
        - Agile promotes the continuous delivery of working software or product features. This delivery can happen in intervals (e.g., every 2-4 weeks), providing users with incremental value.
        - **Benefit**: Frequent delivery allows customers to start benefiting from the product early and gives feedback quickly.
    4. **Close Collaboration between Cross-functional Teams**:
        - Agile encourages strong collaboration between cross-functional teams (e.g., developers, testers, designers, and business analysts) to ensure that all perspectives are considered and the team works toward a common goal.
        - **Benefit**: Close collaboration improves communication, reduces misunderstandings, and accelerates decision-making.
    5. **Scrum and Kanban Methodologies**:
        - These are two popular Agile methodologies that provide frameworks for implementing Agile principles.
    
    ### Scrum
    
    Scrum is a framework used in Agile project management that emphasizes teamwork, accountability, and iterative progress toward a well-defined goal.
    
    - **Premise**: Track progress regularly and adjust as necessary to ensure the project stays on track.
    
    ### Key Concepts in Scrum:
    
    1. **Epic**:
        - An Epic is a larger body of work that is broken down into smaller pieces called user stories. It represents a broad feature or initiative.
    2. **User Story**:
        - A User Story is the smallest unit of work in Scrum, typically written from the perspective of the end-user. It describes what needs to be done and why.
        - Example: "As a user, I want to be able to reset my password so that I can regain access to my account."
    3. **Backlog**:
        - The backlog is a list of tasks, features, or issues that the team needs to work on. It is prioritized by the Product Owner and represents what the team plans to deliver.
        - **Process**: Stories in the backlog move through stages such as "To Do," "In Progress," and "Done."
    4. **Scrum Roles**:
        - **Product Owner**: Defines and prioritizes the backlog to maximize value.
        - **Development Team**: Builds the product according to the backlog and works collaboratively.
        - **Scrum Master**: Facilitates the Scrum process, helps remove impediments, and ensures the team follows Scrum practices.
    5. **Scrum Events**:
        - **Sprint Planning**: At the start of each sprint (typically 2-4 weeks), the team plans what they will complete based on story points and time estimations.
        - **Daily Scrum**: A short, daily meeting where the team discusses progress, plans for the day, and any blockers.
        - **Sprint Review**: Held at the end of a sprint to review what has been completed and plan for the next sprint.
    6. **Scrum Board**:
        - The Scrum Board visualizes the progress of the work. Stories move across columns like "To Do," "In Progress," and "Done."
    
    ### Kanban
    
    Kanban is another Agile framework focused on visualizing work, limiting work in progress, and maximizing flow. Unlike Scrum, it doesn’t enforce strict time limits or sprints.
    
    - **Key Features**:
        - **Visualization**: Kanban uses a visual board (Kanban Board) to represent work items and their status. Tasks move from left to right, across columns like "To Do," "In Progress," and "Done."
        - **No Time Limits**: Unlike Scrum, where tasks are completed within fixed time frames (sprints), Kanban doesn't impose strict time limits. Teams work at a continuous pace and focus on the flow of work.
        - **Focus on Flow**: The goal of Kanban is to maximize the efficiency of the workflow by limiting the amount of work in progress (WIP).
    
    ### Comparison: Scrum vs. Kanban
    
    - **Scrum**:
        - Time-boxed sprints (e.g., 2-4 weeks).
        - Roles and events are well-defined (e.g., Product Owner, Daily Scrum, Sprint Planning).
        - Emphasizes completing a set of tasks in each sprint.
    - **Kanban**:
        - Continuous flow without strict time limits.
        - Focuses on visualizing tasks and limiting WIP to improve efficiency.
        - More flexible in handling new tasks and changes without needing formal planning events.
    
    ### Summary:
    
    - **Agile**: A mindset and principles for flexible and iterative development.
    - **Scrum**: A structured framework with roles, events, and a time-boxed sprint approach.
    - **Kanban**: A flexible framework focusing on workflow visualization and continuous delivery without fixed time frames.

- **JQL (Jira Query Language)** is used to search and filter issues within Jira. It allows for creating complex queries to find specific issues based on different criteria. Here's an overview of key concepts and examples:
    
    ### Key Concepts
    
    - **Fields**: These are specific properties of issues, such as `project`, `status`, `assignee`, `priority`, etc.
    - **Operators**: These define the relationship between fields and values. Common operators include `=`, `!=`, `IN`, `NOT IN`, `>`, `<`, and `~` (for contains).
    - **Functions**: Predefined methods like `currentUser()` or `now()` that return dynamic values.
    - **Keywords**: Special terms like `AND`, `OR`, `ORDER BY`, which are used to build queries.
    
    ### Example Queries
    
    - **Basic Query**: Find all issues in a project:
        - `project = PROJ`
    - **Status Filtering**: Find all issues in a specific status:
        - `status = "In Progress"`
    - **Assignee Filtering**: Find all issues assigned to a specific user:
        - `assignee = "username"`
    - **Using Multiple Conditions**: Combine conditions with `AND` or `OR`:
        - `project = PROJ AND status = "To Do"`
    - **Date Filtering**: Find issues created after a certain date:
        - `created > "2023-01-01"`
            
            
    
    These are links for more jql quries
    
    https://confluence.atlassian.com/jirasoftwareserver/advanced-searching-fields-reference-939938743.html
    
    https://support.atlassian.com/jira-software-cloud/docs/jql-fields/
    

- In Jira, **fields** refer to the properties or attributes of an issue, such as `summary`, `description`, `status`, `assignee`, `priority`, etc. These fields are used to store information about each issue in Jira.
    
    When working with Jira's Python library, fields are accessed as attributes of an issue object. For example, after querying an issue, you can access its fields like `issue.fields.summary`, where `fields` is an object that contains all the attributes of the issue.
    
    ### Example
    
    1. **Accessing Fields**: After retrieving an issue, you can access its fields using dot notation.
        - `issue = jira.issue('PROJ-1')`
        - `print(issue.fields.summary)` (this prints the summary of the issue).
    2. **Common Fields**:
        - `summary`: A short description or title of the issue.
        - `description`: A detailed explanation of the issue.
        - `status`: The current status (e.g., "To Do", "In Progress", "Done").
        - `assignee`: The user assigned to the issue.
        - `priority`: The priority level (e.g., "High", "Medium", "Low").
    3. **Viewing All Fields**: You can view all fields associated with an issue by printing the entire `fields` object:
        - `print(issue.fields)`. This will output all available fields for that particular issue.

- Example in python
    
    ```python
    from jira import JIRA
    user = "<Your-email>"
    api = "You-Api-Key"
    server = "URL-TO-YOUR-JIRA-"
    jira = JIRA(server=server,basic_auth=(user,api))
    issue1 = jira.issue('MOA-137') # MOA-137 will be the issue key  - So you will define the issue key and then whatever you want to do with it 
    print(issue1.fields.summary) # Here is the actions you want to perform on that key
    ```
    

- The **Jira REST API** allows you to interact with Jira programmatically over HTTP. You can use the API to create, update, delete, and retrieve issues, among many other tasks, without having to interact with the Jira UI.
    
    ### Key Concepts of Jira REST API
    
    - **Endpoints**: URLs that represent different resources in Jira. For example, `/rest/api/3/issue` is used to create or retrieve issues.
    - **HTTP Methods**:
        - `GET`: Retrieve data (e.g., get an issue).
        - `POST`: Create new data (e.g., create an issue).
        - `PUT`: Update existing data (e.g., update an issue).
        - `DELETE`: Remove data (e.g., delete an issue).
    - **Authentication**: Typically done using Basic Auth (username and API token) or OAuth.
    - **JSON Format**: Data is sent and received in JSON format. When creating or updating an issue, you'll provide data as JSON in the request body.
    
    ### Example Use Cases
    
    - **Create an Issue**: You can send a `POST` request to the `/rest/api/3/issue` endpoint with a JSON payload containing the issue details.
    - **Get an Issue**: Use a `GET` request to the `/rest/api/3/issue/{issueKey}` endpoint to retrieve details of a specific issue.
    - **Search Issues**: You can use JQL (Jira Query Language) in a `GET` request to search for issues at the `/rest/api/3/search` endpoint.
    
    ### Example REST API Call
    
    To create an issue, you would send a `POST` request to the `https://your-domain.atlassian.net/rest/api/3/issue` endpoint with a JSON payload like:
    
    ```json
    jsonCopy code
    {
      "fields": {
        "project": {
          "key": "PROJ"
        },
        "summary": "New issue created via API",
        "description": "Creating an issue using the Jira REST API",
        "issuetype": {
          "name": "Task"
        }
      }
    }
    
    ```
    
    The API is powerful and can be used to automate many Jira tasks directly from scripts or external applications.
    

# Python Flask

### What is Flask

- **What is Flask**
    
    Flask is classified as a micro framework. It has its own set of tools, technologies, and libraries to help with web application development.
    Flask was created by Armin Ronacher of Pocoo, an international group of Python enthusiasts formed in 2004.
    
    - **Flask**: A lightweight web framework written in Python, used to build web applications quickly and easily. It’s called a "micro-framework" because it doesn’t come with built-in tools like database management or form handling, but it provides flexibility to integrate third-party extensions as needed.
    
    ### Key Features:
    
    - **Minimalistic**: Flask provides the essentials for web development, like routing, request handling, and templates, but leaves out unnecessary complexity.
    - **Flexibility**: Developers can choose their tools and libraries, making Flask highly customizable.
    - **Jinja2 Templates**: Flask uses Jinja2 for rendering HTML templates with Python variables.
    - **Werkzeug**: A comprehensive WSGI (Web Server Gateway Interface) library that powers Flask's request and response handling.
    
    ### Basic Concepts:
    
    1. **Routing**: Flask maps URLs to Python functions. This is done using decorators.
        - Example: `@app.route('/')` binds the URL path `/` to a function.
    2. **Views**: The functions you define for each route are called views. These functions return the content (usually HTML) that the user will see in the browser.
    3. **Templates**: Flask uses Jinja2 to render templates, which allows you to insert Python variables into HTML files.
        - Example: `render_template('index.html')`.
    4. **Request Handling**: Flask handles HTTP methods like GET, POST, PUT, DELETE, etc. You can access form data, query parameters, and more using `request`.
    5. **Flask Extensions**: While Flask is minimal, it can be extended using a variety of Flask extensions (e.g., Flask-SQLAlchemy for databases, Flask-WTF for form handling).
    
    ### Basic Example:
    
    ```python
    pythonCopy code
    from flask import Flask, render_template
    
    app = Flask(__name__)
    
    @app.route('/')
    def home():
        return "Welcome to Flask!"
    
    if __name__ == '__main__':
        app.run(debug=True)
    
    ```
    
    ### How Flask Works:
    
    - **Run the Application**: The application runs on a local development server.
    - **Routing**: When a user visits a URL, Flask maps it to a Python function using the `@app.route()` decorator.
    - **Templates**: Flask renders dynamic content using templates.

### Example Code explanation

```python
from flask import Flask, render_template

app = Flask(__name__)

@app.route('/')  # Maps the root URL ('/') to the index() function
def index():
    return "Welcome to home page"

@app.route('/home')  # Maps '/home' URL to the index_temp() function
def index_temp():
    return render_template('index.html')
```

### **`from flask import render_template`**

- **Purpose**: `render_template` is used to load and display an HTML file.
- Flask expects your HTML files to be in a folder named `templates` at the root of your project.
    
    **For example**:
    
    ```graphql
    project/
    ├── app.py       # Your Flask application
    └── templates/
        └── index.html  # HTML file to be rendered
    
    ```
    
    When you use:
    
    ```python
    return render_template('index.html')
    
    ```
    
    Flask will search for `index.html` inside the `templates` folder and display its contents when the corresponding view is accessed.
    

---

### **2. What is a Flask View?**

- A **Flask view** is any function that you define in your application to handle a specific **request** from the user (e.g., navigating to a URL).
- **Example**:Here, `index` is a Flask view. When someone visits the URL mapped to this view, the function will run and return its result to the browser.
    
    ```python
    def index():
        return "Welcome to the home page"
    
    ```
    

---

### **3. Does a Function Automatically Create a URL?**

No, functions themselves **do not create URLs**. To associate a function with a URL, you need to explicitly map it using a route.

**Example of Routing:**

```python
from flask import Flask, render_template

app = Flask(__name__)

@app.route('/')  # Maps the root URL ('/') to the `index` function
def index():
    return "Welcome to the home page"

@app.route('/home')  # Maps '/home' URL to the `index_temp` function
def index_temp():
    return render_template('index.html')

```

- **Route (`@app.route`)**:
    - Connects a URL (e.g., `/` or `/home`) to a function.
    - When a user visits that URL, Flask executes the corresponding function and displays its result.

---

### **4. What Happens with the Function and URL?**

- When a user visits a mapped URL:
    - Flask runs the **function** associated with that URL.
    - The function can return:
        - **Plain text** (e.g., `"Welcome to the home page"`).
        - **An HTML page** (using `render_template`).
    
    **Example of URL Mappings**:
    
    - `/` → Executes the `index` function.
    - `/home` → Executes the `index_temp` function.

---

### **5. What About the Directory and File Names?**

- The function (`def`) **does not create a file or directory**.
- Instead:
    - The function defines the **logic** or content that will be displayed for the associated URL.
    - The `@app.route()` decorator determines which **URL** maps to which function.
    
    **Example**:
    
    - The function `index_temp()` does not create a directory called `index_temp`.
    - Instead:
        - The URL `/home` (as mapped by `@app.route('/home')`) triggers the `index_temp` function.
        - The function uses `render_template` to return the contents of `index.html`.

---

### **6. Summary: Routing and Views in Flask**

| **Concept** | **Explanation** |
| --- | --- |
| **Flask View** | A Python function that handles a web request and returns a response (text or HTML). |
| **Route** | The URL pattern (e.g., `/` or `/home`) that maps to a specific Flask view. |
| **render_template** | A Flask function to load an HTML file from the `templates` folder and render it in the browser. |
| **Directory/File** | The function does not create directories or files; it only returns content for the mapped URL. |

---

### **How Does This Code Work?**

```python
@app.route('/home')
def index_temp():
    return render_template('index.html')

```

1. When the user visits `http://127.0.0.1:5000/home`, Flask:
    - Executes the `index_temp` function.
    - Uses `render_template` to fetch `index.html` from the `templates` folder.
    - Displays the HTML content of `index.html` in the browser.

### **Overview of Jinja Templates**

**Jinja2** is a powerful templating engine used by Flask to render dynamic content in HTML templates. It allows you to write Python-like expressions directly in your HTML files, enabling you to display data and handle logic.

---

### **Key Features of Jinja Templates**

1. **Dynamic Content Rendering**:
    - Use placeholders to insert data from Python code into an HTML file.
2. **Control Structures**:
    - Use loops and conditionals to display content dynamically.
3. **Template Inheritance**:
    - Create reusable layouts with a base template and extend them in child templates.
4. **Filters**:
    - Modify or format data directly in the template.

---

### **Basic Syntax**

Jinja syntax is enclosed within special delimiters:

- `{{ ... }}`: For expressions to output data (e.g., variables, calculations).
- `{% ... %}`: For control statements like loops and conditionals.
- `{# ... #}`: For comments (not rendered in the output).

---

### **Examples**

### **1. Rendering Variables**

In Python:

```python
from flask import Flask, render_template

app = Flask(__name__)

@app.route('/')
def home():
    return render_template('index.html', name="John", age=25)

```

In `index.html`:

```html
<!DOCTYPE html>
<html>
<head>
    <title>Home</title>
</head>
<body>
    <h1>Welcome, {{ name }}!</h1>
    <p>You are {{ age }} years old.</p>
</body>
</html>

```

- **Output**:
    
    ```sql
    Welcome, John!
    You are 25 years old.
    ```
    

---

### **2. Loops**

In Python:

```python
@app.route('/users')
def users():
    user_list = ['Alice', 'Bob', 'Charlie']
    return render_template('users.html', users=user_list)
```

In `users.html`:

```html
<!DOCTYPE html>
<html>
<head>
    <title>Users</title>
</head>
<body>
    <h1>Users List:</h1>
    <ul>
        {% for user in users %}
        <li>{{ user }}</li>
        {% endfor %}
    </ul>
</body>
</html>
```

- **Output**:
    
    ```diff
    Users List:
    - Alice
    - Bob
    - Charlie
    ```
    

---

### **3. Conditionals**

In Python:

```python
@app.route('/status')
def status():
    logged_in = True
    return render_template('status.html', logged_in=logged_in)
```

In `status.html`:

```html
<!DOCTYPE html>
<html>
<head>
    <title>Status</title>
</head>
<body>
    {% if logged_in %}
        <p>You are logged in.</p>
    {% else %}
        <p>You are logged out.</p>
    {% endif %}
</body>
</html>
```

- **Output**:
    
    ```sql
    You are logged in.
    ```
    

---

### **4. Template Inheritance**

**Base Template** (`base.html`):

```html
<!DOCTYPE html>
<html>
<head>
    <title>{% block title %}My Website{% endblock %}</title>
</head>
<body>
    <header>
        <h1>Header Content</h1>
    </header>
    <main>
        {% block content %}{% endblock %}
    </main>
    <footer>
        <p>Footer Content</p>
    </footer>
</body>
</html>

```

**Child Template** (`home.html`):

```html
e.html' %}

{% block title %}Home{% endblock %}

{% block content %}
    <h2>Welcome to the Home Page!</h2>
{% endblock %}

```

- The `home.html` will extend the layout from `base.html`, replacing the `title` and `content` blocks.

---

### **Jinja Filters**

Filters modify the data before rendering:

- **Uppercase**: `{{ name|upper }}`
- **Lowercase**: `{{ name|lower }}`
- **Default Value**: `{{ variable|default('Default Value') }}`

---

### **Advantages of Jinja Templates**

1. **Separation of Concerns**:
    - Keeps the application logic in Python and presentation logic in templates.
2. **Reusable Layouts**:
    - Use inheritance for modular and maintainable designs.
3. **Dynamic Content**:
    - Render data passed from Flask dynamically.

---

### **Common Use Cases**

- Dynamic websites (e.g., user profiles, e-commerce pages).
- Email templates.
- Dashboard interfaces with data visualizations.

---

**Conclusion**: Jinja templates make it easy to create dynamic, modular, and reusable HTML files in Flask applications. They allow you to render data, handle logic, and build structured layouts efficiently.

### API

- **"An API (Application Programming Interface)** is an interface that allows two software components to communicate with each other. It defines the rules and protocols for this communication, enabling applications, services, or servers to exchange data and perform actions without needing to understand each other's internal workings."
    
    ---
    
    ### Breaking it Down
    
    1. **Key Concept**: Start by explaining that an API is an interface for communication between software components (applications, services, or servers).
    2. **Function**: Mention that it enables interaction by defining rules and protocols, abstracting the complexity of the underlying systems.
    3. **Purpose**: Emphasize that APIs allow different systems to work together without needing to understand the internal details of each other.
        
        You can also give an example if asked for one, such as how a mobile app might use an API to fetch data from a server (like fetching weather information or social media posts).
        
        An interface through which different servers communicate with each other 
        
        Enables two software components to communiate with each other using a set of definition and rotocoles
        
        ### Types of APIs:
        
        - **Web APIs**: These are APIs that allow interaction with web services over HTTP/HTTPS. Common examples include REST APIs and SOAP APIs.
        - **Library APIs**: These allow communication between different software libraries and applications.
        - **Operating System APIs**: These are provided by operating systems to allow applications to interact with system resources like file systems or network connections.
        
        ### Example Use Cases:
        
        - **Web Applications**: A web application might use an API to interact with a backend server to retrieve or update data.
        - **Third-Party Integrations**: APIs allow applications to integrate with third-party services, such as payment gateways, social media platforms, or cloud services.
        - **Mobile Apps**: Mobile apps often use APIs to communicate with remote servers to fetch data like user profiles, weather, or news.
        
        ### Common API Protocols:
        
        - **REST (Representational State Transfer)**: REST APIs use HTTP methods (GET, POST, PUT, DELETE) to interact with resources (e.g., retrieving data, creating records). Data is typically sent and received in JSON format.
        - **SOAP (Simple Object Access Protocol)**: An older protocol for sending structured information over the web using XML.
        - **GraphQL**: A query language for APIs that allows clients to request only the specific data they need.
        
        ### Example of a REST API Request:
        
        To get information about a user from a server, you might send a `GET` request to an endpoint like `/api/users/123`. The server would then respond with data about that user, often in JSON format.
        

### HTTP Methods

- HTTP methods are actions that can be performed on a resource when making requests to a server. These methods tell the server what kind of operation to perform. Here are the most common HTTP methods:
    - **GET**: Used to retrieve data from the server. This method does not change the state of the resource; it just fetches the data.
        - Example: Fetching a list of users from `/api/users`.
    - **POST**: Used to send data to the server to create a new resource. This method typically results in a new record being created on the server.
        - Example: Creating a new user with `/api/users`.
    - **PUT**: Used to update an existing resource on the server. It sends the full updated data to the server.
        - Example: Updating user information at `/api/users/123`.
    - **PATCH**: Used to partially update an existing resource on the server. It sends only the data that needs to be changed.
        - Example: Updating just the email of a user at `/api/users/123`.
    - **DELETE**: Used to delete a resource from the server.
        - Example: Deleting a user at `/api/users/123`.
    
    These methods are commonly used in RESTful APIs to interact with resources on a server.
    
    - **PUT**: Replaces the entire resource with new data.
    - **PATCH**: Updates only specific parts of the resource.
    
    Use `PUT` when you want to update everything, and `PATCH` when you only need to update certain fields.
    

### Using Requests library to interact with web APIs.

- The `requests` library in Python is used for making HTTP requests to communicate with web servers. It is commonly used to interact with web APIs.
    
    ### Basic Concepts of `requests`:
    
    - **Sending HTTP Requests**: You can send various types of HTTP requests (GET, POST, PUT, DELETE, etc.) using the `requests` library.
    - **Handling Responses**: After making a request, you can access the response data, status code, and headers.
    
    ### Example Usage:
    
    1. **Importing the Library**:
        - `import requests`
    2. **Making a GET Request**:
        - `response = requests.get('https://example.com')`
        - Fetches data from the specified URL.
    3. **Making a POST Request**:
        - `response = requests.post('https://example.com', data={'key': 'value'})`
        - Sends data to the server to create or update a resource.
    4. **Handling the Response**:
        - `response.status_code`: Gets the status code (e.g., 200 for success).
        - `response.text`: Retrieves the response content as a string.
        - `response.json()`: Converts the response content to JSON if it's in JSON format.
    
    ```python
    import requests
    url = "https://ipinfo.io/<ip-Adress>/geo"
    response = requests.get(url)
    r_data = response.json()
    
    for i in r_data.items():
        print(i)
    ```
    

### Difference Between Web Servers and Web Frameworks

- 
    
    ### **Web Frameworks**
    
    - **Purpose**: Used to build and define what your web application does. They handle the application's logic, process requests, and generate responses. They’re the “creator” of your application’s behavior and content.
    - **Examples**:
        - **Flask**: A lightweight web framework for Python. It’s used to create the routes and logic of your web application. Think of Flask as the kitchen where the food (responses) is prepared.
        - **Django**: A more feature-rich web framework for Python. It provides more built-in functionalities compared to Flask, such as authentication and an ORM for database management.
    
    ### **Web Servers**
    
    - **Purpose**: Manage and serve the application to users. They handle incoming web requests, serve static files (like images or CSS), and forward dynamic requests to the web application (e.g., Flask or Django) for processing. They act as the “distributor” that ensures users can access your application efficiently.
    - **Examples**:
        - **Apache2**: A popular web server that handles requests and serves content. It can also work as a reverse proxy, passing requests to backend applications like Flask or Django.
        - **Nginx**: Another popular web server known for its high performance and low resource usage. It also acts as a reverse proxy and can handle load balancing and caching.
    
    ### **Analogy**
    
    - **Web Framework (Flask/Django)**: Think of it as the kitchen where the food (responses) is prepared.
    - **Web Server (Apache/Nginx)**: Think of it as the waiter who takes orders (requests) from customers (users), brings them to the kitchen (Flask/Django), and then delivers the food back to the customers.
    
    ### Summary
    
    - **Flask** and **Django** are used to build the functionality of your web application, defining how it processes data and responds to requests.
    - **Apache2** and **Nginx** are used to serve and manage the web application to users, handling incoming traffic, serving static files, and passing dynamic requests to the web framework.

# Vagrant:

- Vagrant is a tool that helps you manage virtualized environments efficiently. It allows developers and DevOps engineers to create and configure lightweight, reproducible, and portable development environments, typically using virtual machines (VMs).
- Think of Vagrant as a way to automate the process of setting up virtual machines and software configurations, so you can easily share and recreate environments without manual setup.

### Overview

Vagrant simplifies the management of virtual environments by automating the creation, configuration, and provisioning of virtual machines. Here's an overview of Vagrant:

### What Vagrant Does:

- **Automates Virtual Machine Setup:** Vagrant helps you create and configure virtual machines using providers like VirtualBox, VMware, or cloud providers like AWS.
- **Reproducible Environments:** Vagrantfiles define your environment, making it easy to recreate the same setup on any machine.
- **Provisioning:** Vagrant can automatically install software and run scripts, setting up your environment exactly as needed.
- **Portability:** Since your entire setup is described in a Vagrantfile, you can share this file, allowing others to set up the same environment with one command.

### Key Components:

- **Vagrantfile:** The configuration file where you define your virtual machine, including operating system, networking, provisioning, etc.
- **Providers:** The platform where Vagrant manages the virtual machines (e.g., VirtualBox, VMware, AWS).
- **Provisioners:** Tools or scripts (e.g., Shell, Ansible, Puppet) that configure your VM once it's created.

### Workflow:

1. **Initialize:** Create a new Vagrantfile using `vagrant init`.
2. **Up:** Start your virtual machine with `vagrant up`. This will download the box (VM template), create the VM, and provision it.
3. **SSH:** Access your VM via SSH using `vagrant ssh`.
4. **Halt:** Shut down the VM with `vagrant halt`.
5. **Destroy:** Remove the VM completely with `vagrant destroy`.

### Use Cases:

- **Development Environments:** Developers can work in isolated, consistent environments without affecting their local machine.
- **Testing:** Vagrant makes it easy to spin up test environments, run tests, and then destroy the environments when done.
- **Collaboration:** Teams can share Vagrantfiles to ensure everyone is working in the same environment.

### Commands

- **`vagrant init`**: Initializes a new Vagrant environment by creating a `Vagrantfile`. < `vagrant init` >
- **`vagrant up`**: Starts and provisions the virtual machine as per the configuration in the `Vagrantfile`. < `vagrant up` >
- **`vagrant ssh`**: Connects to the running virtual machine via SSH. < `vagrant ssh` >
- **`vagrant halt`**: Shuts down the running virtual machine. < `vagrant halt` >
- **`vagrant destroy`**: Removes the virtual machine and all its resources. < `vagrant destroy` >
- **`vagrant status`**: Displays the status of the virtual machine (whether it is running, halted, etc.). < `vagrant status` >
- **`vagrant reload`**: Restarts the virtual machine, applying any changes made to the `Vagrantfile`. < `vagrant reload` >
- **`vagrant provision`**: Runs the provisioners defined in the `Vagrantfile` without recreating the machine. < `vagrant provision` >
- **`vagrant box list`**: Lists all the Vagrant boxes installed on your system. < `vagrant box list` >
- **`vagrant box add`**: Adds a new Vagrant box to your system. < `vagrant box add [box-name]` >
- **`vagrant box remove`**: Removes a Vagrant box from your system. < `vagrant box remove [box-name]` >
- **`vagrant suspend`**: Suspends the virtual machine, saving the current state. < `vagrant suspend` >
- **`vagrant resume`**: Resumes a suspended virtual machine. < `vagrant resume` >
- **`vagrant plugin list`**: Lists all installed Vagrant plugins. < `vagrant plugin list` >
- **`vagrant plugin install`**: Installs a Vagrant plugin. < `vagrant plugin install [plugin-name]` >
- **`vagrant help`**: Displays help information for Vagrant, listing available commands and usage. < `vagrant help` >

### Vagrant Cloud

**Vagrant Cloud** is a platform provided by HashiCorp that allows users to discover, share, and distribute Vagrant boxes. It's a central repository where you can find pre-built Vagrant boxes created by other users or organizations, making it easier to set up environments quickly without needing to configure everything from scratch.

### Key Features:

- **Discover Boxes**: You can search for and download Vagrant boxes created by others to use in your projects. These boxes are often pre-configured with specific software, operating systems, or environments.
- **Host Your Own Boxes**: You can upload and share your own custom Vagrant boxes with the community or your team. This is useful if you've created a specific environment that you want others to use.
- **Versioning**: Vagrant Cloud supports versioning of boxes, so you can update your boxes and manage different versions over time.
- **Private Boxes**: You can host private boxes that are only accessible to specific users or teams, ideal for internal use or company-wide environments.

### Usage:

To use Vagrant Cloud, you generally interact with it through Vagrant itself or the Vagrant Cloud website. For example, you can search for a box and add it to your project with the following commands:

- **`vagrant cloud search`**: Searches for available boxes on Vagrant Cloud. < `vagrant cloud search [box-name]` >
- **`vagrant cloud publish`**: Publishes a new version of your box to Vagrant Cloud. < `vagrant cloud publish [organization/box-name] [version] [provider]` >
- **`vagrant cloud box add`**: Adds a box from Vagrant Cloud to your system. < `vagrant cloud box add [box-name]` >

> **Vagrant** is used to manage virtual machines (VMs), while **Docker** is used to manage containers. VMs are like full operating systems, while containers are lightweight environments that share the host OS kernel.

There are a little bit similar like:
> 
> - **Vagrant box add** ≈ **docker pull** (Downloads the environment).
> - **Vagrant init** is setting up the environment (similar to preparing the configuration in Docker).
> - **Vagrant up** ≈ **docker run** (Starts the environment).
> - **Vagrant ssh** ≈ **docker exec** (Accesses the running environment).

### Vagrant Networking

Vagrant networking allows you to configure how the virtual machine's network behaves, enabling interaction between your Vagrant-managed environment and the outside world, including your host machine or other virtual machines. Here’s an overview of Vagrant networking options:

### 1. **Port Forwarding**

- **Description**: This allows you to access your VM from your host machine through a specific port. For example, you can access a web server running on the VM via `localhost:8080` if port 8080 is forwarded.
- **Syntax**: You can configure port forwarding in your `Vagrantfile` like this:
    - `config.vm.network "forwarded_port", guest: 80, host: 8080`
- **Use Case**: Useful for web development where you need to access a web server running inside the VM from your host machine.

### 2. **Private Network**

- **Description**: This option allows the VM to be accessible only from the host machine, typically for development and testing. The VM will have an IP address assigned to it that only your host machine can access.
- **Syntax**: You can set up a private network like this:
    - `config.vm.network "private_network", ip: "192.168.33.10"`
- **Use Case**: When you need the VM to be reachable from your host but not from the outside world.

### 3. **Public Network**

- **Description**: With a public network, the VM gets an IP address that makes it accessible to other machines on your network (not just the host). This effectively places the VM on the same network as your host machine.
- **Syntax**: You can set up a public network like this:
    - `config.vm.network "public_network"`
- **Use Case**: When you need the VM to be accessible by other devices on the same network as your host machine.

### Example in the `Vagrantfile`

```ruby
rubyCopy code
Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/bionic64"

  # Port forwarding
  config.vm.network "forwarded_port", guest: 80, host: 8080

  # Private network
  config.vm.network "private_network", ip: "192.168.33.10"

  # Public network
  config.vm.network "public_network"
end

```

### Use Cases for Vagrant Networking

- **Port Forwarding**: Ideal for local development when you want to test applications running on your VM from your browser or tools on your host machine.
- **Private Network**: Good for testing environments where the VM needs to simulate a server that only the host machine can access.
- **Public Network**: Useful when multiple VMs need to communicate with each other or when you want to expose your VM to other devices on the same network as your host.

### File Sharing in vagrant

Vagrant file sharing allows you to share folders between your host machine and the virtual machine (VM). This feature is useful for synchronizing files between the two environments, enabling you to edit files on your host and have them reflected in the VM without manual copying.

Here’s an overview of Vagrant file sharing:

### 1. **Synced Folders**

- **Description**: This is the primary way to share files between the host machine and the VM. Vagrant will automatically synchronize a folder on your host machine with a folder on the VM. By default, Vagrant syncs the folder containing the `Vagrantfile` with `/vagrant` inside the VM.
- **Syntax**: You can define custom synced folders in the `Vagrantfile` like this:
    - `config.vm.synced_folder "path/on/host", "/path/on/vm"`
    
    Example:
    
    ```ruby
    rubyCopy code
    Vagrant.configure("2") do |config|
      config.vm.box = "ubuntu/bionic64"
      config.vm.synced_folder "./my_data", "/vagrant_data"
    end
    
    ```
    
    This would sync the `my_data` folder on your host machine to the `/vagrant_data` folder inside the VM.
    
- **Use Case**: Synced folders are ideal for development where you want to work on files locally but need them available inside the VM for testing or running applications.

### 2. **NFS (Network File System)**

- **Description**: Vagrant can also use NFS for file sharing, which is often faster than the default method, especially for large directories or complex file structures.
- **Syntax**: You can enable NFS like this:
    - `config.vm.synced_folder "path/on/host", "/path/on/vm", type: "nfs"`
    
    Example:
    
    ```ruby
    rubyCopy code
    Vagrant.configure("2") do |config|
      config.vm.box = "ubuntu/bionic64"
      config.vm.synced_folder "./my_data", "/vagrant_data", type: "nfs"
    end
    
    ```
    
- **Use Case**: NFS is useful when working with large file systems or when you need better performance for shared folders.

### 3. **rsync**

- **Description**: `rsync` is another option for file sharing in Vagrant. Unlike synced folders that keep files continuously in sync, `rsync` performs a one-way sync from the host to the VM. You have to manually trigger the sync using the `vagrant rsync` command.
- **Syntax**: You can configure `rsync` like this:
    - `config.vm.synced_folder "path/on/host", "/path/on/vm", type: "rsync"`
    
    Example:
    
    ```ruby
    rubyCopy code
    Vagrant.configure("2") do |config|
      config.vm.box = "ubuntu/bionic64"
      config.vm.synced_folder "./my_data", "/vagrant_data", type: "rsync"
    end
    
    ```
    
- **Use Case**: `rsync` is beneficial when you want to avoid continuous synchronization and prefer to manually push updates from your host machine to the VM.

### 4. **SMB (Server Message Block)**

- **Description**: SMB is a file-sharing protocol mainly used on Windows systems, which allows you to share folders between the host and the VM over a network.
- **Syntax**: You can configure SMB like this:
    - `config.vm.synced_folder "path/on/host", "/path/on/vm", type: "smb"`
    
    Example:
    
    ```ruby
    rubyCopy code
    Vagrant.configure("2") do |config|
      config.vm.box = "ubuntu/bionic64"
      config.vm.synced_folder "./my_data", "/vagrant_data", type: "smb"
    end
    
    ```
    
- **Use Case**: SMB is useful for sharing folders between a Windows host and VM, especially when network-based sharing is required.

### Example in the `Vagrantfile`

```ruby
rubyCopy code
Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/bionic64"

  # Default synced folder
  config.vm.synced_folder ".", "/vagrant"

  # Custom synced folder
  config.vm.synced_folder "./my_data", "/vagrant_data"

  # NFS shared folder
  config.vm.synced_folder "./large_data", "/vagrant_large", type: "nfs"

  # rsync shared folder
  config.vm.synced_folder "./static_files", "/vagrant_static", type: "rsync"

  # SMB shared folder
  config.vm.synced_folder "./windows_data", "/vagrant_smb", type: "smb"
end

```

### Use Cases for Vagrant File Sharing

- **Default Synced Folders**: Useful for small projects where you want to work on code locally and see the changes inside the VM.
- **NFS**: Ideal for large projects or when you need better performance for shared folders.
- **rsync**: Useful when you prefer to sync files manually and don’t need continuous synchronization.
- **SMB**: Best for Windows environments that need network-based file sharing.

> If you face network issue like not installing anything using apt-get install in the vm created using vagrant then do the following 
vim /etc/gai.conf —> line 54 or maybe diff —> uncomment or write `precedence ::ffff:0:0/96 100`
> 

### Vagrant Provisioning

**Vagrant provision** is a feature that automates the setup and configuration of your virtual machine (VM) after it's created. Provisioning is the process of preparing the VM with software, services, and settings needed for your development environment. Vagrant supports multiple types of provisioning, such as shell scripts, configuration management tools like Ansible, Chef, Puppet, and more.

Here’s an overview of Vagrant provisioning:

### 1. **Provisioning with Shell Scripts**

- **Description**: You can use shell scripts to provision your VM by running commands inside the VM. This is useful for automating the installation of software, configuring settings, or running any command-line instructions needed for your environment.
- **Syntax**: You define the provisioning shell script in the `Vagrantfile` like this:
    
    ```ruby
    ruby code
    config.vm.provision "shell", path: "script.sh"
    ```
    
    Example:
    
    ```ruby
    Vagrant.configure("2") do |config|
      config.vm.box = "ubuntu/bionic64"
      config.vm.provision "shell", inline: <<-SHELL
        apt-get update
        apt-get install -y apache2
      SHELL
    end
    ```
    
- **Use Case**: This is useful when you need to install software or configure services on the VM right after it's created, without manually logging in to perform these tasks.

### 2. **Provisioning with Ansible**

- **Description**: Ansible is a popular configuration management tool. You can use it with Vagrant to provision your VM by running Ansible playbooks that define how your VM should be configured.
- **Syntax**: Ansible provisioning can be set up like this:
    
    ```ruby
    config.vm.provision "ansible" do |ansible|
      ansible.playbook = "playbook.yml"
    end
    ```
    
- **Use Case**: Ansible is useful for more complex provisioning, especially when you need to manage configurations for multiple servers or environments.

### 3. **Provisioning with Puppet**

- **Description**: Puppet is another configuration management tool. You can use it with Vagrant to automate the configuration of your VM by applying Puppet manifests.
- **Syntax**: You can define Puppet provisioning like this:
    
    ```ruby
    config.vm.provision "puppet" do |puppet|
      puppet.manifests_path = "manifests"
      puppet.manifest_file = "default.pp"
    end
    ```
    
- **Use Case**: Puppet is suitable for more detailed and reusable provisioning logic, especially when you want to apply the same configuration to multiple environments.

### 4. **Provisioning with Chef**

- **Description**: Chef is another configuration management tool, similar to Puppet. You can use Chef with Vagrant to apply cookbooks that define how your VM should be configured.
- **Syntax**: Chef provisioning can be set up like this:
    
    ```ruby
    config.vm.provision "chef_solo" do |chef|
      chef.cookbooks_path = "cookbooks"
      chef.add_recipe "apache"
    end
    ```
    
- **Use Case**: Chef is great for complex configurations, especially when you want to automate the setup of your infrastructure with reusable cookbooks.

### 5. **Running Provisioners**

- **Provisioning on VM creation**: When you run `vagrant up`, Vagrant automatically runs the provisioners defined in the `Vagrantfile` after the VM is created.
- **Manual provisioning**: If you want to re-run provisioning on an already created VM, you can use the `vagrant provision` command.
    - Example: `vagrant provision` (This re-applies the provisioning configuration.)
- **Use Case**: Manual provisioning is helpful when you’ve made changes to your provisioning scripts or tools and need to apply those changes without recreating the VM.

### Example `Vagrantfile` with Multiple Provisioners

```ruby
Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/bionic64"

  # Shell script provisioning
  config.vm.provision "shell", inline: <<-SHELL
    apt-get update
    apt-get install -y apache2
  SHELL

  # Ansible provisioning
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "playbook.yml"
  end
end
```

### Key Commands for Provisioning

- **Provision during creation**: Automatically done when you run `vagrant up`.
- **Manual provision**: Run `vagrant provision` to reapply provisioning.
- **Reprovision with updated configuration**: Run `vagrant reload --provision` to restart the VM and reapply provisioning.

# Ansible

- Ansible is a powerful automation tool designed to simplify the management of IT infrastructure. It automates tasks like software provisioning, configuration management, and application deployment, making it easier to manage large environments with minimal manual intervention.
- Ansible uses a declarative language called YAML to define the desired state of your systems, and it operates over SSH, which means no special software needs to be installed on the machines you're managing.

### Overview of Ansible

**Ansible** is an open-source automation tool used for IT tasks like provisioning, configuration management, and application deployment. It is designed to be simple, agentless, and efficient, using SSH to connect to servers and perform tasks. Ansible helps automate repetitive tasks and manage large-scale infrastructure with ease.

### Key Features of Ansible:

1. **Agentless**: Ansible doesn’t require any software agents on the target machines. It uses SSH (Linux/Unix) or WinRM (Windows) to communicate with servers.
2. **Simple Language (YAML)**: Ansible uses YAML files to define tasks and configurations in an easy-to-read format, called Playbooks.
3. **Idempotency**: Ansible ensures that running a playbook multiple times will result in the same system state, preventing unintended changes.
4. **Modular**: Ansible has many built-in modules for various tasks, such as managing files, services, and packages.

### How Ansible Works:

1. **Control Node**: This is the machine where Ansible is installed. It sends commands to managed nodes (target machines).
2. **Managed Nodes**: These are the target machines that Ansible controls. No software installation is needed on these nodes.
3. **Playbooks**: These are YAML files that define a set of tasks to be executed on the managed nodes. Each playbook is a blueprint for how the infrastructure should look.
4. **Inventory**: A list of managed nodes (servers) that Ansible will communicate with. This can be a simple file listing IP addresses or hostnames.

Ansible is used in DevOps, cloud environments, and IT automation to manage configurations, deploy applications, and handle complex orchestration across multiple servers.

> for installation Guide: [https://docs.ansible.com/ansible/2.9/installation_guide/index.html](https://docs.ansible.com/ansible/2.9/installation_guide/index.html)
> 

### Ansible's architecture

### **1. Control Node:**

- **What it is**: The machine where Ansible is installed and from which commands and playbooks are run.
- **Role**: Acts as the orchestrator. It sends out commands to the managed nodes (target machines) without needing any agent software installed on those nodes.

can also be called ansible engine, controller or master

### **2. Managed Nodes:**

- **What they are**: The machines (servers, network devices, etc.) that Ansible manages. These can be anything from physical servers to virtual machines and cloud instances.
- **Role**: Receive and execute tasks sent from the control node. Managed nodes do not need Ansible installed; they only need Python and SSH (or WinRM for Windows).

### **3. Inventory:**

- **What it is**: A file (typically `hosts` or `inventory.yaml`) that lists the managed nodes (IPs or hostnames). It can also include groups of hosts and their associated variables.
- **Role**: Specifies which machines Ansible will manage. You can define groups of hosts (e.g., web servers, databases) and provide variables specific to each host or group.

### **4. Playbooks:**

- **What they are**: YAML files where you define your tasks, roles, and configurations.
- **Role**: Serve as the blueprint for automation. They contain ordered lists of tasks that Ansible will run on managed nodes. Each playbook consists of one or more "plays" that map hosts to tasks.

### **5. Modules:**

- **What they are**: Small programs that Ansible runs on the managed nodes. Examples include modules for installing software, managing files, or configuring network settings.
- **Role**: Handle specific actions. When a task is executed in a playbook, Ansible runs the corresponding module on the target system. Ansible ships with hundreds of built-in modules, but you can also write your own.

### **6. Plugins:**

- **What they are**: Additional pieces of code that augment Ansible’s core functionality.
- **Role**: Allow you to extend Ansible's capabilities, such as logging output, managing inventories from dynamic sources (e.g., cloud providers), and more.

### **7. Roles:**

- **What they are**: A way to group tasks, variables, files, and handlers into reusable components.
- **Role**: Simplify the organization of playbooks, especially in larger projects. Roles can be reused across different playbooks, making Ansible playbooks more modular and manageable.

### **8. Ansible Galaxy:**

- **What it is**: A repository for Ansible roles, allowing you to share and download roles created by others.
- **Role**: Speeds up development by providing pre-built roles for common tasks like setting up web servers, databases, etc.

### **9. Connection Plugins:**

- **What they are**: Plugins that manage how Ansible connects to managed nodes.
- **Role**: Define the transport method, typically SSH for Unix/Linux and WinRM for Windows, used to connect to target machines.

### **10. Inventory Plugins:**

- **What they are**: Plugins that allow Ansible to dynamically fetch inventory information from various sources, such as cloud providers or external databases.
- **Role**: Dynamically generate the inventory from cloud providers like AWS, Azure, etc., or other external sources.

### **How It Works:**

1. **Ansible Playbook Execution**: You write a playbook (a YAML file) that describes the tasks to be performed on managed nodes.
2. **Inventory Selection**: Ansible looks at the inventory file to determine which hosts to manage.
3. **Connection to Managed Nodes**: Ansible connects to the managed nodes using SSH (or WinRM for Windows) from the control node.
4. **Module Execution**: The control node sends modules to the managed nodes, executes the tasks, and returns the results.
5. **Reporting**: Ansible reports back the status of each task, indicating success or failure.

### Setup

### **Step 1: Install Ansible on CentOS 9**

1. **Enable the EPEL Repository** (Extra Packages for Enterprise Linux):
    - **Command**: `sudo dnf install epel-release`
    - **Purpose**: The EPEL repository contains extra packages, including Ansible.
2. **Install Ansible**:
    - **Command**: `sudo dnf install ansible`
    - **Purpose**: This installs Ansible and its dependencies.
3. **Verify the Installation**:
    - **Command**: `ansible --version`
    - **Purpose**: To confirm that Ansible is installed correctly.

### **Step 2: Configure the Ansible Inventory**

1. **Locate the Inventory File**:
    - Default location: file path `/etc/ansible/hosts`
    - **Purpose**: This file contains the list of managed nodes (hosts) that Ansible will control.
2. **Edit the Inventory File**:
    - **Command**: `sudo nano /etc/ansible/hosts`
    - **Purpose**: Add your managed nodes’ IP addresses or hostnames. You can group hosts (e.g., `[webservers]`, `[dbservers]`).
    
    **Example**:
    
    ```xml
    [webservers]
    192.168.1.100
    192.168.1.101
    
    [dbservers]
    192.168.1.102
    ```
    

### **Step 3: Configure SSH Access**

1. **Set Up SSH Key-Based Authentication**:
    - **Command**: `ssh-keygen` (on the control node)
    - **Purpose**: Generate an SSH key pair.
2. **Copy the SSH Key to Managed Nodes**:
    - **Command**: `ssh-copy-id username@managed_node_ip`
    - **Purpose**: This allows Ansible to connect to the managed nodes via SSH without needing a password each time.

### **Step 4: Test the Connection**

1. **Ping the Managed Nodes**:
    - **Command**: `ansible all -m ping` OR `ansible webserver -m ping` # This will only run the ip in that section
    - **Purpose**: This tests the connection to all managed nodes listed in the inventory. If successful, you will see a `pong` response from each host.
    
    **Example Output**:
    
    ```ruby
    192.168.1.100 | SUCCESS => {
        "changed": false,
        "ping": "pong"
    }
    ```
    

### **Step 5: Run a Simple Playbook**

1. **Create a Playbook File**:
    - **Command**: `nano simple_playbook.yaml`
    - **Purpose**: Write a simple playbook to test Ansible's functionality.
    
    **Example Playbook**:
    
    ```yaml
    ---
    - hosts: webservers
      tasks:
        - name: Install Nginx
          yum:
            name: nginx
            state: present
    ```
    
2. **Run the Playbook**:
    - **Command**: `ansible-playbook simple_playbook.yaml`
    - **Purpose**: Execute the playbook on the managed nodes listed under the `webservers` group.

### **Step 6: Manage Ansible Configuration**

1. **Edit the Configuration File** (Optional):
    - **File Location**: `/etc/ansible/ansible.cfg`
    - **Purpose**: Adjust global settings for Ansible, such as timeout periods, default inventory locations, or remote user settings.

> Location priority for ansible configuration :-
> 
> 
> 1. ANSIBLE_CONFIG ( Env variable )
> 
> 2. ansible.cfg from current directory
> 
> 3. ansible.cfg file available in home directory
> 
> 4. /etc/ansible location (DEFAULT)
> 

### **Basic Ansible Commands**

- **`ansible <group> -m <module> -a "<arguments>"`**: Runs a module on a specified group of hosts.
    - **Example**: `ansible webservers -m ping` (pings all hosts in the 'webservers' group)
- **`ansible-playbook <playbook.yml>`**: Executes a playbook to automate tasks on hosts.
    - **Example**: `ansible-playbook site.yml` (runs the `site.yml` playbook)
- **`ansible-config`**: Manages and validates Ansible configuration files.
    - **`ansible-config view`**: Views the current Ansible configuration.
    - **`ansible-config dump`**: Shows all configuration options.
    - **`ansible-config init`**: Generates a new Ansible configuration file (`ansible.cfg`).
- **`ansible-doc <module>`**: Provides detailed documentation for a module.
    - **Example**: `ansible-doc copy` (shows documentation for the `copy` module)
- **`ansible-inventory`**: Manages and displays the inventory of hosts.
    - **`ansible-inventory --list`**: Lists all hosts in the inventory.
    - **`ansible-inventory --graph`**: Displays a graph of the inventory structure.
- **`ansible-vault`**: Manages encrypted files and variables.
    - **`ansible-vault create <file>`**: Creates a new encrypted file.
    - **`ansible-vault edit <file>`**: Edits an encrypted file.
    - **`ansible-vault encrypt <file>`**: Encrypts an existing file.
    - **`ansible-vault decrypt <file>`**: Decrypts an encrypted file.
- **`ansible-galaxy`**: Manages roles and collections from Ansible Galaxy.
    - **`ansible-galaxy install <role/collection>`**: Installs a role or collection.
    - **`ansible-galaxy list`**: Lists installed roles and collections.
    - **`ansible-galaxy init <role_name>`**: Creates a new role directory structure.
- **`ansible-pull -U <repository>`**: Pulls and runs a playbook from a VCS repository.
    - **Example**: `ansible-pull -U https://github.com/user/repo.git` (pulls the playbook from the repository and runs it)

### **Help Command**

- **`ansible --help`**: Shows help for Ansible, listing all the available commands and options.
    - **`ansible-doc -l`**: Lists all available modules.

> Watch this yt video for better understanding:
[https://youtu.be/5hycyr-8EKs?si=IE1_RPMdJedOZd4b](https://youtu.be/5hycyr-8EKs?si=IE1_RPMdJedOZd4b)
> 

### **Ad-Hoc Command in Ansible**

Ansible Ad-Hoc commands allow you to run quick, one-off tasks on remote hosts without needing to create a full playbook. These are useful for performing simple tasks like pinging hosts, copying files, or restarting services.

### **Syntax**

The basic syntax for an Ad-Hoc command is:

- **`ansible <group> -m <module> -a "<arguments>"`**: This is the general structure of an Ad-Hoc command.
    - **`<group>`**: The group of hosts on which you want to run the command (e.g., `webservers`, `all`).
    - **`m <module>`**: Specifies the module you want to use (e.g., `ping`, `shell`, `copy`).
    - **`a "<arguments>"`**: Provides the arguments required by the module (e.g., command to run, source and destination for copying).

### **Examples of Ad-Hoc Commands**

- **Ping All Hosts**: Test connectivity to all hosts in the inventory.
    - **Example**: `ansible all -m ping`
- **Run a Shell Command**: Run a shell command on a group of hosts.
    - **Example**: `ansible webservers -m shell -a "uptime"`
- **Copy a File**: Copy a file to a remote host.
    - **Example**: `ansible dbservers -m copy -a "src=/local/path/file.txt dest=/remote/path/file.txt"`
- **Restart a Service**: Restart a service on remote hosts.
    - **Example**: `ansible webservers -m service -a "name=httpd state=restarted"`
- **Install a Package**: Install a package using the package manager.
    - **Example**: `ansible all -m yum -a "name=nginx state=present"` (for RHEL-based systems)

### **Important Flags for Ad-Hoc Commands**

- **`i <inventory>`**: Specify a custom inventory file.
    - **Example**: `ansible all -i /path/to/inventory -m ping`
- **`u <user>`**: Specify the remote user to use.
    - **Example**: `ansible all -u aadmin -m ping`
- **`b`**: Run the command with `sudo`.
    - **Example**: `ansible all -b -m yum -a "name=nginx state=present"`

### **Common Ansible Command Flags**

Here are some frequently used flags in Ansible, explained in the inline format:

- **`i <inventory>`**: Specify the inventory file to use. By default, Ansible uses `/etc/ansible/hosts` as the inventory file.
    
    *Example*: `ansible all -i /path/to/inventory -m ping`
    
- **`u <user>`**: Define the remote user to connect to the hosts.
    
    *Example*: `ansible all -u aadmin -m ping`
    
- **`k`**: Prompt for the SSH password of the remote user. This is useful when you are not using SSH keys for authentication.
    
    *Example*: `ansible all -m ping -k`
    
- **`K`**: Prompt for the `sudo` password of the remote user. This is required if you want to use `sudo` and the remote user requires a password for sudo operations.
    
    *Example*: `ansible all -b -m ping -K`
    
- **`b`**: Run the command with `sudo`. This elevates the command to root privileges.
    
    *Example*: `ansible all -b -m yum -a "name=nginx state=present"`
    
- **`m <module>`**: Specify the Ansible module to use.
    
    *Example*: `ansible all -m ping`
    
- **`a <arguments>`**: Pass arguments to the module being executed.
    
    *Example*: `ansible all -m shell -a "uptime"`
    
- **`-check`**: Perform a "dry run" without making actual changes. This is helpful to see what would happen without modifying anything.
    
    *Example*: `ansible all -m yum -a "name=nginx state=present" --check`
    
- **`v`, `vv`, `vvv`, `vvvv`**: Increase verbosity of the command output. More `v`s provide more detailed output.
    
    *Example*: `ansible all -m ping -vv`
    
- **`-limit <subset>`**: Limit the execution to a subset of hosts. This can be a single host or a group of hosts.
    
    *Example*: `ansible all --limit webservers -m ping`
    
- **`e <extra_vars>`**: Pass additional variables to the playbook or command.
    
    *Example*: `ansible-playbook playbook.yml -e "var1=value1 var2=value2"`
    

### **Difference Between `command` and `shell` Modules in Ansible**

- **`command` Module**:
    
    **Description**: Executes commands on the remote system without invoking a shell. This means it doesn't support shell features like pipes (`|`), redirection (`>`, `<`), or environment variable expansion (`$VAR`). It is safer since it avoids potential shell injection vulnerabilities.
    
    **When to Use**: Use the `command` module when you want to run simple commands that don't require shell-specific features.
    
    **Example**: `ansible all -m command -a "uptime"`
    
    This will run the `uptime` command on all hosts.
    
- **`shell` Module**:
    
    **Description**: Executes commands through the system's shell (`/bin/sh` by default). This allows you to use shell features like pipes, redirection, and environment variables. It offers more flexibility but is also more prone to security risks if user input isn't properly sanitized.
    
    **When to Use**: Use the `shell` module when you need to use shell features, like chaining commands with `&&`, using pipes, or environment variable expansion.
    
    **Example**: `ansible all -m shell -a "echo $HOME && uptime"`
    
    This will run both commands through the shell on all hosts.
    

### **Key Points**:

- **Security**: The `command` module is more secure because it doesn't use a shell. The `shell` module can be riskier due to potential shell injection vulnerabilities.
- **Flexibility**: The `shell` module offers more flexibility because it allows complex command constructs, whereas `command` is limited to straightforward commands.

### **Using Ansible to Manage Packages with `apt` and `yum`**

Ansible can be used to manage packages on remote systems through the `apt` and `yum` modules. These modules allow you to install, remove, or update packages on Debian-based (like Ubuntu) and Red Hat-based (like CentOS, RHEL) systems, respectively.

### **1. Using `apt` Module (Debian/Ubuntu Systems)**

- **Install a package**:
    - **Command**: Installs a package on Debian-based systems.
    - **Example**:`ansible all -m apt -a "name=nginx state=present"`This installs the `nginx` package on all hosts.
- **Remove a package**:
    - **Command**: Removes a package.
    - **Example**:`ansible all -m apt -a "name=nginx state=absent"`This removes the `nginx` package on all hosts.
- **Update a package**:
    - **Command**: Updates the specified package.
    - **Example**:`ansible all -m apt -a "name=nginx state=latest"`This ensures the `nginx` package is at the latest version on all hosts.
- **Update the package cache**:
    - **Command**: Updates the package list before installing/updating packages.
    - **Example**:`ansible all -m apt -a "update_cache=yes"`This updates the package cache on all hosts.

### **2. Using `yum` Module (RHEL/CentOS Systems)**

- **Install a package**:
    - **Command**: Installs a package on Red Hat-based systems.
    - **Example**:`ansible all -m yum -a "name=httpd state=present"`This installs the `httpd` (Apache) package on all hosts.
- **Remove a package**:
    - **Command**: Removes a package.
    - **Example**:`ansible all -m yum -a "name=httpd state=absent"`This removes the `httpd` package on all hosts.
- **Update a package**:
    - **Command**: Updates the specified package.
    - **Example**:`ansible all -m yum -a "name=httpd state=latest"`This ensures the `httpd` package is at the latest version on all hosts.
- **Update all packages**:
    - **Command**: Updates all packages to the latest version.
    - **Example**:`ansible all -m yum -a "name=* state=latest"`This updates all packages on all hosts to their latest versions.

### **Key Points**

- **State**: The `state` parameter is crucial in both `apt` and `yum` modules. You can use:
    - **`present`**: To install a package.
    - **`absent`**: To remove a package.
    - **`latest`**: To ensure the package is updated to its latest version.
- **Update Package List**:
    - For `apt`, you may need to update the package list (`update_cache`) before installing or updating packages. This is not required for `yum`.
- sudo:
    - use `-b` to use sudo e.g `ansible all -m yum -a "name=* state=latest" -b`

### Ansible Modules

### **System Management Modules**

- **`user`**: Manages user accounts. < `ansible -m user -a "name=username state=present"` >
- **`group`**: Manages groups on remote hosts. < `ansible -m group -a "name=groupname state=present"` >
- **`cron`**: Manages cron jobs. < `ansible -m cron -a "name=backup job='tar czf /tmp/backup.tgz /home/'"` >
- **`service`**: Manages system services. < `ansible -m service -a "name=httpd state=started"` >
- **`package`**: Manages packages using the appropriate package manager for the system. < `ansible -m package -a "name=httpd state=present"` >
- `setup`: Displays all the facts/information

### **File Management Modules**

- **`copy`**: Copies files to remote locations. < `ansible -m copy -a "src=/local/file dest=/remote/file"` >
- **`file`**: Manages file properties (permissions, ownership, etc.). < `ansible -m file -a "path=/path/to/file mode=0755"` >
- **`template`**: Deploys Jinja2 templates. < `ansible -m template -a "src=/local/template.j2 dest=/remote/template.conf"` >
- **`fetch`**: Fetches files from remote hosts. < `ansible -m fetch -a "src=/remote/file dest=/local/dir"` > # you can use the `flat=yes` Flag in the end to only copy the specified and without the Directories with ip (Structure)

### **Networking Modules**

- **`ping`**: Tests connectivity between Ansible and the target host. < `ansible -m ping all` >
- **`firewalld`**: Manages firewall rules using `firewalld`. < `ansible -m firewalld -a "service=http zone=public state=enabled permanent=true"` >
- **`iptables`**: Manages iptables rules. < `ansible -m iptables -a "chain=INPUT protocol=tcp destination_port=22 jump=ACCEPT"` >

### **Cloud Management Modules**

- **`ec2`**: Manages AWS EC2 instances. < `ansible -m ec2 -a "region=us-west-2 image=ami-123456 state=present"` >
- **`gce`**: Manages Google Cloud instances. < `ansible -m gce -a "name=my-instance zone=us-central1-a state=present"` >
- **`azure_rm`**: Manages Azure resources. < `ansible -m azure_rm -a "resource_group=myResourceGroup name=myVM state=present"` >

### **Database Modules**

- **`mysql_db`**: Manages MySQL databases. < `ansible -m mysql_db -a "name=mydb state=present"` >
- **`postgresql_db`**: Manages PostgreSQL databases. < `ansible -m postgresql_db -a "name=mydb state=present"` >

### **Command and Shell Modules**

- **`command`**: Executes a command on a remote host. < `ansible -m command -a "ls /var/www"` >
- **`shell`**: Executes a shell command on a remote host. < `ansible -m shell -a "echo 'Hello World'"` >
- **`script`**: Runs a local script on remote hosts. < `ansible -m script -a "/path/to/script.sh"` >

### **Miscellaneous Modules**

- **`yum`**: Manages packages on RedHat-based systems. < `ansible -m yum -a "name=httpd state=present"` >
- **`apt`**: Manages packages on Debian-based systems. < `ansible -m apt -a "name=nginx state=present"` >
- **`git`**: Manages Git repositories. < `ansible -m git -a "repo=https://github.com/repo.git dest=/path/to/repo"` >

### **Facts in Ansible**

**Facts** in Ansible are pieces of information about the remote systems managed by Ansible. These can include details like the hostname, IP address, OS version, memory, and more. Facts are gathered automatically by the `setup` module and are available for use in playbooks, templates, and other parts of an Ansible run.

- **Gathering Facts**: Ansible automatically gathers facts when you run a playbook unless you disable fact gathering. You can explicitly gather facts using the `setup` module. < `ansible -m setup all` >
- **Using Facts**: You can use facts in your playbooks by referencing them in templates, tasks, or conditionals. For example, `ansible_facts['ansible_hostname']` retrieves the hostname of the target system.

### **Custom Facts**

Custom facts allow you to define your own facts beyond the default ones provided by Ansible. These facts are stored in a file on the remote system and can be written in various formats such as INI, JSON, or executable scripts (e.g., Python, Shell).

- **Creating Custom Facts**: Custom facts are stored in the `/etc/ansible/facts.d/` directory on the remote system. You can create your own custom fact files in this directory.
    - For example, create an INI file named `custom.fact` in `/etc/ansible/facts.d/` with content like:
        
        ```csharp
        [custom_info]
        my_custom_fact = my_value
        ```
        
- **Accessing Custom Facts**: After setting up custom facts, they can be accessed in the same way as regular facts in your playbook, using `ansible_local` namespace. < `ansible_facts['ansible_local']['custom_info']['my_custom_fact']` >
- **Example Playbook Usage**:
    
    ```yaml
    - name: Print custom fact
      hosts: all
      tasks:
        - name: Display my custom fact
          debug:
            msg: "{{ ansible_local.custom_info.my_custom_fact }}"
    ```
    

### **Why Use Custom Facts?**

Custom facts are useful when you need to store and retrieve system-specific data that isn't provided by default facts. This can include:

- Configuration settings that vary across environments.
- Information about applications installed on the system.
- Custom tags for categorizing systems.
- `ansible all -m setup -a "filter=ansible_local"` # Use this command to view the output of the script ran using add-hoc commands
#**NOTE:** the script should also be in the node machine’s `/etc/ansible/facts.d/` and have the permissions to be executed

### Ansible Playbooks

Ansible Playbooks are YAML files that define a series of tasks for configuring systems, deploying applications, and managing services in an automated way. They are a powerful tool in Ansible for executing multiple tasks in sequence across your infrastructure.

### **Structure of an Ansible Playbook**

A basic Ansible Playbook consists of **plays**, and each play defines the tasks to be executed on a group of hosts.

- **Play**: A play maps a group of hosts to a set of roles or tasks.
- **Tasks**: A task is a unit of action in Ansible (e.g., install a package, copy a file).
- **Handlers**: Special tasks that run when triggered by other tasks (e.g., restarting a service after configuration changes).

### **Basic Structure**

```yaml
yamlCopy code
---
- name: Description of the Playbook
  hosts: all
  become: true
  tasks:
    - name: Ensure Apache is installed
      yum:
        name: httpd
        state: present

    - name: Start Apache service
      service:
        name: httpd
        state: started
```

### **Key Elements Explained**

- **`name:`**: Describes what the play or task is doing. This is useful for readability.
- **`hosts:`**: Specifies which hosts or groups of hosts the playbook should run on.
- **`become:`**: This is used to escalate privileges, usually to root, using `sudo`. Setting this to `true` ensures that the tasks are run with elevated privileges.
- **`tasks:`**: Lists all the tasks that will be executed in this play. Each task has a `name` and an Ansible module (e.g., `yum`, `service`).
- **`handlers:`**: These are special tasks that get triggered when notified by other tasks (e.g., restarting a service when a configuration file is changed).

### **Running Playbooks**

You run a playbook using the `ansible-playbook` command. For example:

```bash
ansible-playbook site.yml
```

### **Sample Playbook: Setting Up a Web Server**

```yaml
yamlCopy code
---
- name: Setup Apache Web Server on CentOS
  hosts: webservers
  become: true
  tasks:
    - name: Install Apache
      yum:
        name: httpd
        state: present

    - name: Start Apache service
      service:
        name: httpd
        state: started
        enabled: true

    - name: Copy index.html to web server
      copy:
        src: /path/to/index.html
        dest: /var/www/html/index.html

    - name: Open HTTP port in firewall
      firewalld:
        port: 80/tcp
        permanent: true
        state: enabled
        immediate: true

  handlers:
    - name: Restart Apache
      service:
        name: httpd
        state: restarted
```

### **Explanation**

- **`yum` module**: Installs or removes packages.
- **`service` module**: Manages the state of services.
- **`copy` module**: Copies files to the target hosts.
- **`firewalld` module**: Manages firewall rules using `firewalld`.

### **Common Ansible Playbook Commands**

1. **`ansible-playbook`**: Run a playbook.
    - Example: `ansible-playbook site.yml`
2. **`i <inventory>`**: Specify the inventory file/hosts-file. 
    - Example: `ansible-playbook site.yml -i inventory`
3. **`-limit <hostname>`**: Run the playbook on a specific host or group of hosts.
    - Example: `ansible-playbook site.yml --limit webservers`
4. **`e <extra-vars>`**: Pass extra variables to the playbook.
    - Example: `ansible-playbook site.yml -e "version=2.0"`
5. **`-check`**: Run the playbook in check mode (dry run).
    - Example: `ansible-playbook site.yml --check`

### **Advanced Concepts**

- **Roles**: Organize playbooks into reusable sets of files and tasks.
- **Variables**: Use variables to manage dynamic values in your playbooks.
- **Conditionals**: Run tasks based on conditions, such as the output of previous tasks.
- **Loops**: Iterate over items in a list or range.

Ansible Playbooks allow you to define infrastructure as code and automate your operations. By combining different modules, variables, and roles, you can create highly efficient and reusable configurations for your environments.

> You can use online yml validators to check if the yml syntax is correct or not 
just google: yml validator  and open anyone you like
> 

### More Elements in Playbooks

```yaml
---
- name: Ensure Apache is installed and running with additional settings
  hosts: all
  become: true
  gather_facts: true

  vars:
    apache_package: httpd
    apache_service: httpd

  environment:
    PATH: "/usr/local/bin:/usr/bin:/bin"

  tasks:
    - name: Ensure Apache is installed
      yum:
        name: "{{ apache_package }}"
        state: present
      register: apache_install_result

    - name: Debug the installation result
      debug:
        var: apache_install_result

    - name: Start Apache service
      service:
        name: "{{ apache_service }}"
        state: started
      notify:
        - Restart Apache service

  handlers:
    - name: Restart Apache service
      service:
        name: "{{ apache_service }}"
        state: restarted

  tags:
    - apache
    - webserver
```

### **Key Elements Explained**

- **`name:`**: Describes what the play or task is doing. This is useful for readability.
- **`hosts:`**: Specifies which hosts or groups of hosts the playbook should run on.
- **`become:`**: Used to escalate privileges, usually to root, using `sudo`. Setting this to `true` ensures that the tasks are run with elevated privileges.
- **`gather_facts:`**: When set to `true`, it gathers system facts (like OS, IP addresses) from the managed hosts before running the tasks. This is enabled by default.
- **`vars:`**: Defines variables that can be used throughout the playbook. For example, `apache_package` and `apache_service` are variables used in the tasks.
- **`vars_files:`**: Allows you to include external YAML files containing variables. These files are loaded and the variables can be used throughout the playbook.
    - Example:
        
        ```yaml
        vars_files:
          - /path/to/variables.yml
        ```
        
- **`environment:`**: Sets environment variables for the tasks. For example, you can modify the `PATH` environment variable to include custom paths.
- **`tasks:`**: Lists all the tasks that will be executed in this play. Each task has a `name` and an Ansible module (e.g., `yum`, `service`).
- **`register:`**: Stores the result of a task in a variable. This is useful for capturing the output of a task to use later in the playbook.
    - Example: `register: apache_install_result`
- **`debug:`**: Prints out variables or data for debugging purposes. It helps to display the contents of variables during playbook execution.
    - Example: `debug: var: apache_install_result`
- **`notify:`**: Triggers a handler to perform an action when a task changes. In this example, if the Apache service is started, the handler to restart the service is notified.
- **`handlers:`**: These are special tasks that get triggered when notified by other tasks (e.g., restarting a service when a configuration file is changed).
- **`tags:`**: Allows you to group tasks with tags, making it easier to run or skip specific tasks. For example, you can run tasks related to the `apache` tag or the `webserver` tag.

### When in Ansible-Playbooks

The `when` clause in Ansible is used to control the execution of tasks based on conditions. It allows you to run tasks only when certain conditions are met. Here’s a detailed look at how it works:

### **Basic Syntax**

```yaml
- name: Task Name
  <module>:
    <module_parameters>
  when: <condition>
```

### **Examples**

### **1. Conditional Execution Based on a Variable**

If you want to run a task only if a certain variable is defined, you can use:

```yaml
- name: Ensure a file is present
  file:
    path: /path/to/file
    state: touch
  when: some_variable is defined
```

### **2. Conditional Execution Based on a Fact**

You might want to execute a task only if the system meets certain criteria, like checking the OS family:

```yaml
- name: Install package on Debian-based systems
  apt:
    name: vim
    state: present
  when: ansible_os_family == "Debian"
```

### **3. Multiple Conditions**

You can combine multiple conditions using logical operators:

```yaml
- name: Install package on RedHat-based systems if not already installed
  yum:
    name: vim
    state: present
  when:
    - ansible_os_family == "RedHat"
    - version is defined
```

### **4. Using `when` with `register`**

The `when` clause can be used in conjunction with the `register` directive to check the result of a previously executed task:

```yaml
- name: Check if apache2 or httpd is installed
  shell: apache2 -v || httpd -v
  register: version_output

- name: Print version information
  debug:
    var: version_output.stdout
  when: version_output.stdout != ""
```

### **Common Use Cases**

- **Conditional Execution**: Execute tasks based on facts or variables.
- **Skip Tasks**: Skip tasks if certain conditions are not met.
- **Handling Different Environments**: Run specific tasks only on certain operating systems or environments.

### Data Types in Ansible

### **1. Strings**

- **Description**: A sequence of characters enclosed in quotes.
- **Example**:
    
    ```yaml
    name: "John Doe"
    greeting: 'Hello, world!'
    ```
    

### **2. Integers**

- **Description**: Whole numbers without decimal points.
- **Example**:
    
    ```yaml
    port: 80
    max_connections: 1000
    ```
    

### **3. Floats**

- **Description**: Numbers with decimal points.
- **Example**:
    
    ```yaml
    version: 1.2
    timeout: 0.5
    ```
    

### **4. Booleans**

- **Description**: Represents `true` or `false` values.
- **Example**:
    
    ```yaml
    enabled: true
    debug: false
    ```
    

### **5. Lists (Arrays)**

- **Description**: Ordered collections of items. Items can be of any type, and lists are defined using square brackets.
- **Example**:
    
    ```yaml
    ports:
      - 80
      - 443
    servers:
      - "web01.example.com"
      - "web02.example.com"
    ```
    

### **6. Dictionaries (Hash Maps)**

- **Description**: Unordered collections of key-value pairs. Dictionaries are defined using curly braces.
- **Example**:
    
    ```yaml
    database:
      name: "mydb"
      user: "admin"
      password: "secret"
    ```
    

### **YAML Syntax Overview**

1. **Lists (Arrays) in YAML**
    - **Description**: Ordered collections of items. Each item is listed on a new line with a leading hyphen (`-`).
    - **Example**:
        
        ```yaml
        ports:
          - 80
          - 443
        servers:
          - "web01.example.com"
          - "web02.example.com"
        ```
        
    
    In this YAML example:
    
    - `ports` is a list containing two items: `80` and `443`.
    - `servers` is a list containing two items: `"web01.example.com"` and `"web02.example.com"`.
    
    YAML does not require explicit square brackets for lists; it uses a more human-readable format with hyphens.
    
2. **Dictionaries (Hash Maps) in YAML**
    - **Description**: Unordered collections of key-value pairs. Each key-value pair is defined on a new line with a colon (`:`) separating the key and value.
    - **Example**:
        
        ```yaml
        database:
          name: "mydb"
          user: "admin"
          password: "secret"
        ```
        
    
    In this YAML example:
    
    - `database` is a dictionary (or map) containing three key-value pairs:
        - `name` has the value `"mydb"`.
        - `user` has the value `"admin"`.
        - `password` has the value `"secret"`.
    
    YAML uses indentation to represent nested dictionaries and lists, making the structure easy to read and understand.
    

### **7. Null Values**

- **Description**: Represents the absence of a value. In YAML, this is often represented as `null` or simply omitted.
- **Example**:
    
    ```yaml
    optional_value: null
    ```
    

### **8. YAML Tags and Aliases**

- **Description**: YAML supports custom tags and aliases for reusing data. Aliases refer to previously defined values.
- **Example**:
    
    ```yaml
    defaults: &defaults
      port: 80
      timeout: 30
    
    server1:
      <<: *defaults
      name: "server1"
    
    server2:
      <<: *defaults
      name: "server2"
    ```
    

### **Usage in Playbooks**

### **Example of Using Different Data Types**

```yaml
---
- name: Example playbook demonstrating various data types
  hosts: all
  vars:
    string_example: "This is a string"
    integer_example: 100
    float_example: 10.5
    boolean_example: true
    list_example:
      - item1
      - item2
    dict_example:
      key1: "value1"
      key2: 42
  tasks:
    - name: Display all variables
      debug:
        msg: |
          String Example: {{ string_example }}
          Integer Example: {{ integer_example }}
          Float Example: {{ float_example }}
          Boolean Example: {{ boolean_example }}
          List Example: {{ list_example }}
          Dict Example: {{ dict_example }}
    - name: Add a number to an integer
      debug:
        msg: "The result of adding 10 to integer_example is {{ integer_example + 10 }}"
```

### **Key Points**

- **Consistency**: Ensure that the data types used in your playbooks are consistent with what your modules and tasks expect.
- **Type Casting**: Ansible can handle implicit type conversions, but it’s good practice to explicitly cast variables if needed.
- **Validation**: Use validation techniques to ensure variables are of the expected type to avoid runtime errors.

### **9. Complex Dictionaries (Nested Hash Maps)**

- **Description**: Dictionaries that contain other dictionaries or lists, allowing for more complex data structures.
- **Example**:
    
    ```yaml
    server_config:
      database:
        name: "mydb"
        user: "admin"
        password: "secret"
      networks:
        - name: "internal"
          cidr: "192.168.1.0/24"
        - name: "external"
          cidr: "10.0.0.0/24"
    ```
    

### **10. Complex Lists (Nested Arrays)**

- **Description**: Lists that contain other lists or dictionaries, providing more complex data structures.
- **Example**:
    
    ```yaml
    
    servers:
      - name: "server1"
        ip: "192.168.1.10"
        roles:
          - web
          - db
      - name: "server2"
        ip: "192.168.1.11"
        roles:
          - web
    ```
    

### **11. JSON Structures**

- **Description**: JSON data can be used directly in YAML. JSON structures are essentially the same as dictionaries and lists in YAML.
- **Example**:
    
    ```yaml
    json_data: |
      {
        "name": "example",
        "values": [1, 2, 3],
        "details": {
          "type": "test",
          "status": "active"
        }
      }
    ```
    

### **12. Multiline Strings**

- **Description**: Strings that span multiple lines. YAML supports two types: folded (`>`) and literal (`|`).
- **Example**:
    
    ```yaml
    folded_style: >
      This is a folded
      multiline string.
      Newlines are converted to spaces.
    
    literal_style: |
      This is a literal
      multiline string.
      Newlines are preserved.
    ```
    

### **13. YAML Tags**

- **Description**: Tags are used to explicitly specify the type of data. For instance, `!!python/str` for strings or `!!python/float` for floats.
- **Example**:
    
    ```yaml
    string_with_tag: !!python/str "This is explicitly a string"
    float_with_tag: !!python/float 1.23
    ```
    

### **14. Variables**

- **Description**: Variables can be used to dynamically change values in your playbooks based on conditions or inputs.
- **Example**:
    
    ```yaml
    vars:
      service_name: "nginx"
    
    tasks:
      - name: Install the service
        package:
          name: "{{ service_name }}"
          state: present
    ```
    

### **15. Environment Variables**

- **Description**: Variables defined at the environment level that can be used within playbooks.
- **Example**:
    
    ```yaml
    tasks:
      - name: Print environment variable
        debug:
          msg: "The HOME environment variable is {{ lookup('env', 'HOME') }}"
    ```
    

### **16. Ansible Facts**

- **Description**: Collected information about the managed hosts, which can be used in tasks.
- **Example**:
    
    ```yaml
    tasks:
      - name: Print OS family
        debug:
          msg: "The OS family is {{ ansible_facts['os_family'] }}"
    ```
    

### **17. Jinja2 Templates**

- **Description**: Jinja2 is used for templating in Ansible. Variables can be substituted in strings using Jinja2 syntax.
- **Example**:
    
    ```yaml
    tasks:
      - name: Create a configuration file
        template:
          src: "config.j2"
          dest: "/etc/myapp/config.conf"
    ```
    

### **Example Jinja2 Template (config.j2)**

```
server {
    listen {{ port }};
    server_name {{ server_name }};
}
```

### **18. Ansible Lookup Plugins**

- **Description**: Allows you to fetch data from different sources.
- **Example**:
    
    ```yaml
    tasks:
      - name: Read a file content
        debug:
          msg: "{{ lookup('file', 'path/to/file.txt') }}"
    ```
    

### **Filters in Ansible**

Filters in Ansible are used to modify or format data in templates or playbooks. They are applied using the pipe `|` symbol.

### **1. default**

- **Description**: Provides a default value if the variable is undefined or empty.
- **Usage**: `{{ variable | default('default_value') }}`

### **2. length**

- **Description**: Returns the length of a list, string, or dictionary.
- **Usage**: `{{ list_variable | length }}`

### **3. to_json**

- **Description**: Converts a variable to a JSON formatted string.
- **Usage**: `{{ variable | to_json }}`

### **4. to_yaml**

- **Description**: Converts a variable to a YAML formatted string.
- **Usage**: `{{ variable | to_yaml }}`

### **5. split**

- **Description**: Splits a string into a list based on a delimiter.
- **Usage**: `{{ "a,b,c" | split(',') }}`

### **6. join**

- **Description**: Joins a list into a single string with a specified delimiter.
- **Usage**: `{{ list_variable | join(',') }}`

### **7. replace**

- **Description**: Replaces occurrences of a substring in a string with another substring.
- **Usage**: `{{ "string to be replaced" | replace('to be replaced', 'replaced') }}`

### **8. regex_search**

- **Description**: Searches for a regular expression pattern in a string and returns the first match.
- **Usage**: `{{ "string with numbers 123" | regex_search('\d+') }}`

### **9. regex_replace**

- **Description**: Replaces occurrences of a regular expression pattern in a string with a new string.
- **Usage**: `{{ "string with numbers 123" | regex_replace('\d+', 'number') }}`

### **10. dict2items**

- **Description**: Converts a dictionary to a list of key-value pairs (useful for iteration).
- **Usage**: `{{ dict_variable | dict2items }}`

### **11. items2dict**

- **Description**: Converts a list of key-value pairs into a dictionary.
- **Usage**: `{{ list_of_pairs | items2dict }}`

### **12. type_debug**

- **Description**: Provides the type of a variable (useful for debugging).
- **Usage**: `{{ variable | type_debug }}`

### **13. unique**

- **Description**: Removes duplicate elements from a list.
- **Usage**: `{{ list_variable | unique }}`

### **14. sort**

- **Description**: Sorts a list.
- **Usage**: `{{ list_variable | sort }}`

### **15. map**

- **Description**: Applies a filter or transformation to each item in a list.
- **Usage**: `{{ list_variable | map('filter_name', 'argument') }}`

### **Examples in a Playbook**

```yaml
yamlCopy code
---
- hosts: localhost
  tasks:
    - name: Example of default filter
      debug:
        msg: "{{ undefined_variable | default('Default Value') }}"

    - name: Example of length filter
      debug:
        msg: "{{ ['item1', 'item2', 'item3'] | length }}"

    - name: Example of to_json filter
      debug:
        msg: "{{ {'key': 'value'} | to_json }}"

    - name: Example of split filter
      debug:
        msg: "{{ 'a,b,c' | split(',') }}"

    - name: Example of replace filter
      debug:
        msg: "{{ 'Replace this text' | replace('this', 'that') }}"

    - name: Example of regex_search filter
      debug:
        msg: "{{ 'Find numbers 123' | regex_search('\\d+') }}"

    - name: Example of unique filter
      debug:
        msg: "{{ ['a', 'b', 'a'] | unique }}"

    - name: Example of sort filter
      debug:
        msg: "{{ [3, 1, 2] | sort }}"

```

Each filter serves a different purpose and can be combined with others to transform data as needed in your playbooks.

### Set_facts and diff with vars

**`set_facts`** is an Ansible module that allows you to dynamically set variables (facts) during the execution of a playbook. Once set, these facts are available for use in subsequent tasks within the same playbook.

### Key Characteristics of `set_facts`:

- **Dynamic Assignment**: You can assign or modify variables based on conditions or calculations that occur during the playbook execution.
- **Task-Level Scope**: The variables set with `set_facts` are valid for the duration of the playbook execution.
- **Overriding Existing Facts**: `set_facts` can override previously gathered facts or variables.

**Example Usage**:

```yaml
- name: Set a dynamic fact
  set_facts:
    my_dynamic_fact: "value"
```

### Difference Between `vars` and `set_facts`:

- **`vars`**:
    - **Definition**: Static variables defined at the beginning of a playbook, task, or role.
    - **Scope**: Available throughout the entire playbook or role.
    - **Usage**: Best for values that do not need to change during playbook execution.
    - **Example**:
        
        ```yaml
        vars:
          static_variable: "value"
        ```
        
- **`set_facts`**:
    - **Definition**: Dynamic variables (facts) that are set or modified during the playbook execution.
    - **Scope**: Valid for the duration of the playbook but can be set or updated dynamically based on logic or conditions.
    - **Usage**: Ideal for when you need to set or modify values dynamically based on runtime conditions.
    - **Example**:
        
        ```yaml
        - name: Set dynamic fact based on condition
          set_facts:
            dynamic_variable: "{{ calculated_value }}"
        ```
        

### Summary:

- **`vars`**: Static variables defined at the start, available throughout the playbook.
- **`set_facts`**: Dynamic variables set or updated during playbook execution, used for more flexible scenarios.

### User input

In Ansible, taking input from a user can be done using the `vars_prompt` feature, which prompts the user for input during playbook execution. You can also control whether the input should be visible (public) or hidden (private).

### `vars_prompt`

This feature prompts the user for input, which can be used as variables in the playbook.

### Basic Example of `vars_prompt`

```yaml
- hosts: localhost
  vars_prompt:
    - name: "user_name"
      prompt: "Please enter your name"

  tasks:
    - name: Display user input
      debug:
        msg: "Hello, {{ user_name }}!"
```

- **`name`**: The variable name that will store the user's input.
- **`prompt`**: The message that will be displayed to the user when asking for input.

### Private Input (Hidden Input)

To take input from a user and hide what they type (e.g., for passwords), you can use the `private: yes` option.

### Example with Hidden Input

```yaml
- hosts: localhost
  vars_prompt:
    - name: "user_password"
      prompt: "Please enter your password"
      private: yes

  tasks:
    - name: Display password input (for demonstration, normally you wouldn't display passwords)
      debug:
        msg: "Your password is {{ user_password }}"
```

- **`private: yes`**: Ensures that the input is hidden (useful for sensitive information like passwords).

### Public Input (Visible Input)

By default, input is public (visible), but if you want to explicitly make sure that the input is visible, you can set `private: no`.

### Example with Public Input

```yaml
- hosts: localhost
  vars_prompt:
    - name: "user_city"
      prompt: "Please enter your city"
      private: no  # This is the default behavior, input will be visible

  tasks:
    - name: Display city input
      debug:
        msg: "You are from {{ user_city }}"
```

### Summary:

- **`private: yes`**: Hides the input (e.g., for passwords).
- **`private: no`**: Makes the input visible (default behavior).

### Passing Variables through cli

In Ansible, you can pass variable values from the command line using the `--extra-vars` (or `-e`) flag. This allows you to override variables defined in the playbook or set new ones.

### Basic Syntax

To pass variables via the command line, use the following syntax:

```python
ansible-playbook playbook.yml --extra-vars "variable_name=value"
```

### Examples

1. **Passing a Single Variable:**
    
    ```bash
    ansible-playbook playbook.yml --extra-vars "user_name=John"
    ```
    
    In this case, the `user_name` variable will be set to `John`.
    
2. **Passing Multiple Variables:**
You can pass multiple variables by separating them with spaces.
    
    ```bash
    ansible-playbook playbook.yml --extra-vars "user_name=John user_age=30"
    ```
    
3. **Passing Variables as JSON:**
If you have many variables, you can pass them as a JSON string.
    
    ```bash
    ansible-playbook playbook.yml --extra-vars '{"user_name": "John", "user_age": 30}'
    ```
    
4. **Using Variables in the Playbook:**
Here's how you would use the passed variables in your playbook:
    
    ```yaml
    - hosts: localhost
      tasks:
        - name: Print the user's name and age
          debug:
            msg: "User name is {{ user_name }} and age is {{ user_age }}"
    ```
    

### Notes:

- **Priority**: Variables passed via `-extra-vars` have the highest priority and will override variables defined in playbooks, roles, or inventory.
- **Security**: Be cautious when passing sensitive data (e.g., passwords) as command-line arguments, as they may be visible in process listings. In such cases, consider using `vars_prompt` or `vault` for better security.

### Ansible Operators

Ansible operators are used to perform various operations within playbooks, such as logical, arithmetic, and comparison operations. These operators are similar to those found in other programming languages like Python. Below is an overview of common operators in Ansible:

### 1. **Arithmetic Operators**

- **`+`**: Adds two numbers.
    - Example: `{{ 5 + 3 }}` results in `8`.
- **`-`**: Subtracts the second number from the first.
    - Example: `{{ 5 - 3 }}` results in `2`.
- **`*`**: Multiplies two numbers.
    - Example: `{{ 5 * 3 }}` results in `15`.
- **`/`**: Divides the first number by the second.
    - Example: `{{ 9 / 3 }}` results in `3`.
- **`%`**: Returns the remainder of division (modulo).
    - Example: `{{ 10 % 3 }}` results in `1`.
- **`**`**: Exponentiation (power).
    - Example: `{{ 2 ** 3 }}` results in `8`.

### 2. **Comparison Operators**

- **`==`**: Checks if two values are equal.
    - Example: `{{ 5 == 5 }}` results in `True`.
- **`!=`**: Checks if two values are not equal.
    - Example: `{{ 5 != 3 }}` results in `True`.
- **`>`**: Checks if the left value is greater than the right.
    - Example: `{{ 5 > 3 }}` results in `True`.
- **`<`**: Checks if the left value is less than the right.
    - Example: `{{ 5 < 8 }}` results in `True`.
- **`>=`**: Checks if the left value is greater than or equal to the right.
    - Example: `{{ 5 >= 5 }}` results in `True`.
- **`<=`**: Checks if the left value is less than or equal to the right.
    - Example: `{{ 5 <= 8 }}` results in `True`.

### 3. **Logical Operators**

- **`and`**: Returns `True` if both conditions are true.
    - Example: `{{ (5 > 3) and (8 > 6) }}` results in `True`.
- **`or`**: Returns `True` if at least one condition is true.
    - Example: `{{ (5 > 3) or (8 < 6) }}` results in `True`.
- **`not`**: Negates a condition (reverses its boolean value).
    - Example: `{{ not (5 > 3) }}` results in `False`.

### 4. **Membership Operators**

- **`in`**: Checks if an item exists in a list or a string.
    - Example: `{{ 'item1' in ['item1', 'item2'] }}` results in `True`.
- **`not in`**: Checks if an item does not exist in a list or a string.
    - Example: `{{ 'item3' not in ['item1', 'item2'] }}` results in `True`.

### 5. **Jinja2 Control Structures**

- **`if` / `elif` / `else`**: Conditional statements to control the flow of tasks.
    - Example:
        
        ```yaml
        - debug:
            msg: "Condition met"
          when: ansible_os_family == "Debian"
        ```
        

### 6. **Ternary Operator**

- A shorthand for `if-else` conditionals.
- Example: `{{ 'yes' if condition else 'no' }}`

**Example playbook that incorporates arithmetic, comparison, logical, and other operations**

```yaml
---
- hosts: localhost
  vars_prompt:
    - name: c
      prompt: "Enter the C value:"
      private: no
    - name: d
      prompt: "Enter the D value:"
      private: no
  vars:
    a: 10
    b: 5
    name1: "Abdeali"
    name2: "Dodiya"
    lists: [1, 4, 8, 4, 2, 16]
    my_lists:
      - one
      - two
      - three
  tasks:
    - name: Arithmetic operators
      debug:
        msg:
          - "Addition: {{ a + b }}"  # 10 + 5 = 15
          - "C + D total is: {{ c|int + d|int }}"  # User-provided values added together
          - "Subtraction: {{ a - b }}"  # 10 - 5 = 5
          - "Multiplication: {{ a * b }}"  # 10 * 5 = 50
          - "Division: {{ a / b }}"  # 10 / 5 = 2.0
          - "Modulus: {{ a % b }}"  # 10 % 5 = 0
          - "Exponentiation: {{ a ** b }}"  # 10^5 = 100000

    - name: Comparison operators
      debug:
        msg:
          - "Is a equal to b? {{ a == b }}"  # False
          - "Is a not equal to b? {{ a != b }}"  # True
          - "Is a less than b? {{ a < b }}"  # False
          - "Is a greater than b? {{ a > b }}"  # True
          - "Is a less than or equal to b? {{ a <= b }}"  # False
          - "Is a greater than or equal to b? {{ a >= b }}"  # True
          - "Is name1 in 'Abdeali'? {{ name1 in 'Abdeali' }}"  # True
          - "Is a > 5 or b > 10? {{ a > 5 or b > 10 }}"  # True
          - "Max value in list: {{ lists | max }}"  # 16
          - "Min value in list: {{ lists | min }}"  # 1
          - "Lowercase name1: {{ name1 | lower }}"  # abdeali
          - "Uppercase name1: {{ name1 | upper }}"  # ABDEALI
          - "Title case name1: {{ name1 | title }}"  # Abdeali
          - "Replace 'a' with 'A' in name1: {{ name1 | replace('a', 'A') }}"  # AbdeAli
          - "Join my_lists: {{ my_lists | join(', ') }}"  # one, two, three

```

### Explanation of the Playbook:

1. **`vars_prompt`**: Prompts the user to input values for variables `c` and `d`. The input is not private (visible).
2. **`vars`**: Predefines variables such as `a`, `b`, `name1`, `name2`, `lists`, and `my_lists`.
3. **`tasks`**: Contains two main sections:
    - **Arithmetic Operators**: Demonstrates arithmetic operations, including addition, subtraction, multiplication, division, modulus, and exponentiation.
    - **Comparison Operators**: Demonstrates comparison operations, logical conditions, and string manipulations.

### Expected Output:

When you run this playbook, you will be prompted to enter values for `c` and `d`. The output would look like this, assuming `c=3` and `d=7` were entered:

```yaml
TASK [Arithmetic operators]
ok: [localhost] => {
    "msg": [
        "Addition: 15",
        "C + D total is: 10",
        "Subtraction: 5",
        "Multiplication: 50",
        "Division: 2.0",
        "Modulus: 0",
        "Exponentiation: 100000"
    ]
}

TASK [Comparison operators]
ok: [localhost] => {
    "msg": [
        "Is a equal to b? False",
        "Is a not equal to b? True",
        "Is a less than b? False",
        "Is a greater than b? True",
        "Is a less than or equal to b? False",
        "Is a greater than or equal to b? True",
        "Is name1 in 'Abdeali'? True",
        "Is a > 5 or b > 10? True",
        "Max value in list: 16",
        "Min value in list: 1",
        "Lowercase name1: abdeali",
        "Uppercase name1: ABDEALI",
        "Title case name1: Abdeali",
        "Replace 'a' with 'A' in name1: AbdeAli",
        "Join my_lists: one, two, three"
    ]
}
```

This example shows how to utilize different operators, string manipulations, and list operations in Ansible.

### Loops in Ansible

Loops in Ansible allow you to repeat a task for multiple items, which is useful for tasks like bulk creation, configuration, or managing similar resources. Ansible provides a simple way to iterate over lists using the `loop` directive.

Here’s an example of using loops in Ansible with a task that creates multiple users:

```yaml
---
- hosts: rhel
  become: yes
  vars:
    my_bulk_users:
      - username: abdeali
        password: Admin@123
      - username: kazim
        password: Admin@123
      - username: ali
        password: Admin@123
  tasks:
    - name: Bulk user creation
      user:
        name: "{{ item.username }}"
        password: "{{ item.password | password_hash('sha512') }}"
        update_password: on_create
      loop: "{{ my_bulk_users }}"
```

### Explanation:

- **`loop`**: This is the directive used to iterate over a list. In this case, it loops over the `my_bulk_users` list.
- **`{{ item.username }}`** and **`{{ item.password }}`**: Access individual items from the loop. Here, each `item` is a dictionary with `username` and `password` keys.
- **`password_hash('sha512')`**: This hashes the password using the `sha512` algorithm, which is required for securely storing passwords.

### Types of Loops in Ansible:

1. **Simple Loop**: Loops over a list of items (as shown above).
    - `loop: "{{ my_bulk_users }}"`
2. **With Index**: Use `with_indexed_items` if you need an index with each item.
    - Example: `with_indexed_items: "{{ my_bulk_users }}"`
3. **Looping over Dictionaries**: Use `with_dict` to loop over key-value pairs in a dictionary.
    - Example: `with_dict: "{{ my_dict }}"`
4. **Nested Loops**: You can nest loops by combining lists or dictionaries.
    - Example:
        
        ```yaml
        - name: Nested loops
          debug:
            msg: "User {{ item[0].username }} and Group {{ item[1].groupname }}"
          with_nested:
            - "{{ my_bulk_users }}"
            - "{{ my_groups }}"
        ```
        

### Understanding Loops in Ansible

Loops in Ansible are a powerful way to automate repetitive tasks, like creating multiple users or managing multiple resources. The concept is similar to loops in programming languages, where you perform the same operation for each item in a list or sequence.

Let’s break it down step by step:

### 1. **Basic Concept of Loops**

When you have a set of items (e.g., users, files, packages) that you want to process in the same way, you can use a loop. Instead of writing the same task multiple times, you define the task once and loop over the items.

### 2. **How Loops Work in Ansible**

In Ansible, loops work by iterating over each item in a list (or other iterable objects) and executing the task for each item. **Ansible automatically sets the variable** `item` to the current value in the loop during each iteration.

Here’s a simplified explanation using the previous example:

```yaml
- hosts: rhel
  become: yes
  vars:
    my_bulk_users:
      - username: abdeali
        password: Admin@123
      - username: kazim
        password: Admin@123
      - username: ali
        password: Admin@123
  tasks:
    - name: Bulk user creation
      user:
        name: "{{ item.username }}"
        password: "{{ item.password | password_hash('sha512') }}"
        update_password: on_create
      loop: "{{ my_bulk_users }}"

```

### 3. **Step-by-Step Breakdown**

- **`my_bulk_users` Variable**: This is a list of dictionaries, where each dictionary represents a user with a `username` and `password`.
    
    ```yaml
    my_bulk_users:
      - username: abdeali
        password: Admin@123
      - username: kazim
        password: Admin@123
      - username: ali
        password: Admin@123
    ```
    
- **Task Definition**: You define a single task to create a user using the `user` module. Instead of hardcoding the `name` and `password`, you use `{{ item.username }}` and `{{ item.password }}`. `item` will represent each user dictionary during each iteration of the loop.
- **Loop Directive**: `loop: "{{ my_bulk_users }}"` tells Ansible to iterate over the `my_bulk_users` list. For each iteration, `item` will be set to the current user dictionary.
- **First Iteration**:
    - `item` is set to `{username: 'abdeali', password: 'Admin@123'}`
    - The task creates the user `abdeali` with the hashed password.
- **Second Iteration**:
    - `item` is set to `{username: 'kazim', password: 'Admin@123'}`
    - The task creates the user `kazim` with the hashed password.
- **Third Iteration**:
    - `item` is set to `{username: 'ali', password: 'Admin@123'}`
    - The task creates the user `ali` with the hashed password.

Ansible handles the iteration for you, so you only need to define the task once.

### 4. **Key Terms**

- **`item`**: A special variable that represents the current item in the loop.
- **`loop`**: The directive used to specify what list or iterable to loop over.

### Example:

Let’s imagine you want to send out a notification for each user you created. Instead of writing a task for each user, you would use a loop to send the notification for each `item` in `my_bulk_users`.

```yaml
- name: Notify about user creation
  debug:
    msg: "User {{ item.username }} has been created."
  loop: "{{ my_bulk_users }}"

```

Here, the `debug` task will print a message for each user in `my_bulk_users`.

### Summary

- **Loops in Ansible** allow you to repeat a task for multiple items.
- **`item`** is the variable that holds the value of the current item in the loop.
- You use the **`loop` directive** to tell Ansible what list or sequence to iterate over.
- Loops help you automate repetitive tasks and handle dynamic data efficiently.

### Handling multiple loops

To handle multiple lists or dictionaries in a loop, you can use `loop_control` to manage different loop variables. This way, you can work with complex data structures without confusion over the `item` variable.

### Example: Looping Through Multiple Lists/Dictionaries

Here’s a scenario where we loop through two different lists, one containing user details and another containing groups. We’ll also use `loop_control` to rename the loop variables for clarity.

```yaml
---
- hosts: rhel
  become: yes
  vars:
    my_bulk_users:
      - username: abdeali
        password: Admin@123
      - username: kazim
        password: Admin@123
      - username: ali
        password: Admin@123

    my_groups:
      - groupname: admin
      - groupname: dev
      - groupname: qa

  tasks:
    - name: Bulk user creation
      user:
        name: "{{ user_item.username }}"
        password: "{{ user_item.password | password_hash('sha512') }}"
        update_password: on_create
      loop: "{{ my_bulk_users }}"
      loop_control:
        loop_var: user_item  # Rename 'item' to 'user_item' for clarity

    - name: Bulk group creation
      group:
        name: "{{ group_item.groupname }}"
      loop: "{{ my_groups }}"
      loop_control:
        loop_var: group_item  # Rename 'item' to 'group_item' for clarity
```

### Explanation:

1. **`my_bulk_users`:** This list contains dictionaries with user details (username and password).
2. **`my_groups`:** This list contains dictionaries with group names.
3. **`loop_control`:** We rename `item` to `user_item` and `group_item` for each loop to differentiate between the loops.
4. **First Task (User Creation):**
    - The loop iterates over `my_bulk_users`.
    - Each iteration assigns the current user dictionary to `user_item`.
    - The `user` module creates a user using `user_item.username` and `user_item.password`.
5. **Second Task (Group Creation):**
    - The loop iterates over `my_groups`.
    - Each iteration assigns the current group dictionary to `group_item`.
    - The `group` module creates a group using `group_item.groupname`.

### How This Works in the Background:

- **Loop 1:** Ansible iterates over `my_bulk_users`, assigning each dictionary (user details) to `user_item` and executing the `user` module for each user.
- **Loop 2:** After Loop 1 completes, Ansible starts Loop 2, iterating over `my_groups`, assigning each dictionary (group details) to `group_item`, and executing the `group` module for each group.

This setup allows you to handle multiple lists or dictionaries within the same playbook without conflicts between loop variables.

### Understanding ansible loop using python example

### Concept of Loops in Ansible Tasks

- **Ansible Task**: In Ansible, tasks are actions that you want to perform on your managed nodes. Tasks are executed in the order they are written, and each task defines what should be done (e.g., create a user, install a package).
- **Loop in Tasks**: When you want to repeat a task multiple times with different inputs (like creating multiple users), you use a loop. The loop allows you to iterate over a list or dictionary and apply the task to each item in that list or dictionary.

### How Loops Work in Ansible

1. **Task Definition**: You define the task that you want to repeat (e.g., creating a user).
2. **Loop Declaration**: Instead of repeating the task manually, you use the `loop` keyword to define the list or dictionary you want to iterate over. Ansible will automatically execute the task for each item in the loop.
3. **Item Variable**: During each iteration, Ansible temporarily assigns the current item in the loop to a variable named `item`. You can use `item` to refer to the current element of the list or dictionary.
4. **Task Execution**: Ansible executes the task once for each item in the list or dictionary, using the `item` variable to reference the specific data for that iteration.

### Example Breakdown

In the example you provided earlier:

```yaml
---
- hosts: rhel
  become: yes
  vars:
    my_bulk_users:
      - username: abdeali
        password: Admin@123
      - username: kazim
        password: Admin@123
      - username: ali
        password: Admin@123
  tasks:
  - name: Bulk user creation
    user:
      name: "{{ item.username }}"
      password: "{{ item.password | password_hash('sha512') }}"
      update_password: on_create
    loop: "{{ my_bulk_users }}"
```

- **Task**: The task is defined to create a user using the `user` module.
- **Loop**: The `loop` keyword is used to iterate over the list `my_bulk_users`.
- **Item Variable**: During each iteration, `item` will represent one dictionary from the `my_bulk_users` list (e.g., `{username: abdeali, password: Admin@123}`).
- **Task Execution**: The `user` module task is executed three times—once for each dictionary in the list. During each iteration, `item.username` and `item.password` refer to the current dictionary's values.

### Multiple Lists or Dictionaries

If you have multiple lists or dictionaries, you can use `with_items`, `loop`, or `loop_control` for advanced handling. Ansible handles each loop separately, and each `item` refers to the current element of that loop. If you're dealing with nested loops or complex data structures, you might need to use more advanced techniques like `subelements` or combining dictionaries.

### in Python terms! Here's how it maps to Ansible:

- In Python, you would write something like this:

```python
my_bulk_users = [
    {'username': 'abdeali', 'password': 'Admin@123'},
    {'username': 'kazim', 'password': 'Admin@123'},
    {'username': 'ali', 'password': 'Admin@123'}
]

for item in my_bulk_users:
    name = item['username']
    password = item['password']
    # Perform some action with name and password(Like, User creation)
```

- In Ansible, the concept is similar, but instead of explicitly writing out the loop and the logic in the same way as Python, you tie the loop to a task using the `loop` keyword:

```yaml
- hosts: rhel
  become: yes
  vars:
    my_bulk_users:
      - username: abdeali
        password: Admin@123
      - username: kazim
        password: Admin@123
      - username: ali
        password: Admin@123
  tasks:
  - name: Bulk user creation
    user:
      name: "{{ item.username }}"
      password: "{{ item.password | password_hash('sha512') }}"
      update_password: on_create
    loop: "{{ my_bulk_users }}"
```

So, in your Ansible playbook:

1. **Ansible's loop**: It's like the `for` loop in Python. Ansible iterates over each element in `my_bulk_users`.
2. **`item` variable**: In each iteration, `item` holds one dictionary from the list (just like `item` in your Python `for` loop). So, `item['username']` in Python becomes `item.username` in Ansible.

To break it down further:

- Ansible goes through each dictionary in `my_bulk_users`.
- It assigns the dictionary to `item`.
- It then uses `item.username` and `item.password` within the task.

The task is executed once for each user in `my_bulk_users`.

### Ansible Vaults

Ansible Vault is a feature of Ansible that allows you to encrypt sensitive data, such as passwords, API keys, and other credentials, to protect them from unauthorized access. This is particularly useful when sharing playbooks or storing them in version control systems (like GitHub).

### Key Concepts of Ansible Vault:

1. **Encrypting Files**: Ansible Vault can encrypt entire files, like playbooks, variable files, or even custom scripts.
2. **Decrypting Files**: When running playbooks, Ansible can automatically decrypt files as long as it has access to the decryption key or password.
3. **Editing Encrypted Files**: You can securely edit encrypted files without decrypting them manually, and Ansible will handle the encryption after editing.
4. **Encrypting Variable Values**: Ansible Vault can encrypt only specific variables instead of the entire file.

### Common Ansible Vault Commands:

- **Encrypting a File**: To encrypt a file using Ansible Vault:
    - `ansible-vault encrypt <filename>`
    - This command will prompt you to set a password to protect the file.
- **Decrypting a File**: To decrypt a previously encrypted file:
    - `ansible-vault decrypt <filename>`
    - You will be prompted to enter the password.
- **Editing an Encrypted File**: To securely edit an encrypted file:
    - `ansible-vault edit <filename>`
    - The file is decrypted temporarily for editing, and then encrypted again when saved.
- **Encrypting Specific Variables in a Playbook**: You can encrypt only sensitive variable values within a file using:
    - `ansible-vault encrypt_string '<string_value>' --name <variable_name>`
    - This allows only the specified variable to be encrypted, rather than the entire file.
- **Rekeying (Changing the Password)**: If you need to change the password on an encrypted file:
    - `ansible-vault rekey <filename>`

### Using Vault in Playbooks:

When you have encrypted variables in your playbooks, you'll need to provide the password when running the playbook so that Ansible can decrypt the values. You can do this in several ways:

- **Interactive Password Prompt**: You will be prompted for the vault password when running the playbook:
    - `ansible-playbook <playbook.yml> --ask-vault-pass`
- **Password File**: You can specify a password file (which should be protected) to avoid being prompted interactively:
    - `ansible-playbook <playbook.yml> --vault-password-file <password_file>`

### Example Workflow:

### 1. Encrypting a Variable File:

Let's say you have a variables file called `secrets.yml` with sensitive data, such as database passwords.

To encrypt it:

- Run `ansible-vault encrypt secrets.yml`.
- Enter the password when prompted.

Now, `secrets.yml` is encrypted and cannot be read without the password.

### 2. Using Encrypted Variables in a Playbook:

In your playbook, you can reference variables from `secrets.yml` just like any other variables. When running the playbook, Ansible will decrypt the file automatically if you provide the correct password.

```yaml
---
- hosts: all
  vars_files:
    - secrets.yml  # This file is encrypted with Ansible Vault
  tasks:
    - name: Use the encrypted password in a task
      debug:
        msg: "The database password is {{ db_password }}"
```

When running the playbook:

- `ansible-playbook playbook.yml --ask-vault-pass`

This will prompt you for the vault password, allowing Ansible to decrypt `secrets.yml`.

### Advantages of Using Ansible Vault:

- **Security**: Sensitive information like passwords and API keys are protected by encryption, preventing accidental leaks or unauthorized access.
- **Integration**: Vault works seamlessly with existing Ansible workflows, including playbooks and roles.
- **Flexibility**: You can encrypt entire files, or just specific variables, depending on your needs.

### Considerations:

- **Password Management**: You need to securely manage and share the vault password, especially in team environments.
- **Complexity**: Encrypting multiple files and variables can add complexity, so it’s important to balance security with usability.

### Ansible roles

Ansible roles are a powerful feature designed to help organize and reuse Ansible playbooks. They provide a structured way to group tasks, handlers, variables, and other components into reusable units. Roles promote modularity and help manage complexity in large playbooks.

### Key Concepts of Ansible Roles:

1. **Role Directory Structure**: Each role has a specific directory structure that includes various components like tasks, handlers, templates, and defaults. This structure helps in organizing related files and makes roles easily reusable.
2. **Tasks**: Define the steps to be executed by the role. Tasks are typically defined in the `tasks/main.yml` file.
3. **Handlers**: Special tasks that are triggered by other tasks. Handlers are defined in `handlers/main.yml` and are used for actions like restarting services.
4. **Defaults**: Default variables for the role are defined in `defaults/main.yml`. These variables can be overridden by variables defined in playbooks or other roles.
5. **Vars**: Additional variables that can be defined in `vars/main.yml`. Unlike defaults, these variables are not meant to be overridden.
6. **Templates**: Jinja2 templates used for configuration files or other dynamic content are stored in the `templates/` directory.
7. **Files**: Static files that need to be copied to the managed machines are stored in the `files/` directory.
8. **Meta**: Metadata about the role, such as dependencies on other roles, is defined in `meta/main.yml`.

### Example Role Directory Structure:

```css
my_role/
├── defaults/
│   └── main.yml
├── files/
│   └── myfile.conf
├── handlers/
│   └── main.yml
├── meta/
│   └── main.yml
├── tasks/
│   └── main.yml
├── templates/
│   └── mytemplate.j2
└── vars/
    └── main.yml
```

### Example Role Components:

- **defaults/main.yml**:
    
    ```yaml
    ---
    # Default variables
    my_variable: "default_value"
    ```
    
- **vars/main.yml**:
    
    ```yaml
    ---
    # Role-specific variables
    my_special_variable: "special_value"
    ```
    
- **tasks/main.yml**:
    
    ```yaml
    ---
    - name: Ensure a package is installed
      apt:
        name: "{{ package_name }}"
        state: present
    
    - name: Start a service
      service:
        name: "{{ service_name }}"
        state: started
    ```
    
- **handlers/main.yml**:
    
    ```yaml
    ---
    - name: restart my service
      service:
        name: "{{ service_name }}"
        state: restarted
    ```
    
- **templates/mytemplate.j2**:
    
    ```
    # This is a template file
    config_value = {{ my_variable }}
    ```
    
- **files/myfile.conf**:
    
    ```
    # This is a static file
    ```
    
- **meta/main.yml**:
    
    ```yaml
    ---
    dependencies:
      - another_role
    ```
    

### Using Roles in Playbooks:

To use a role in a playbook, you specify it under the `roles` section. You can also pass variables to the role if needed.

**Example Playbook**:

```yaml
---
- hosts: all
  roles:
    - my_role
```

**Example Playbook with Role Variables**:

```yaml
---
- hosts: all
  roles:
    - role: my_role
      vars:
        package_name: "nginx"
        service_name: "nginx"
```

### Advantages of Using Roles:

- **Modularity**: Roles help break down complex tasks into smaller, manageable pieces.
- **Reusability**: Roles can be reused across different playbooks and projects.
- **Organization**: The structured directory layout of roles keeps files organized and easy to find.
- **Shareability**: Roles can be shared between different teams or projects, improving collaboration.

### Considerations:

- **Role Dependencies**: When using roles that depend on other roles, manage these dependencies carefully to ensure proper order and functionality.
- **Variable Precedence**: Understand the precedence of variables to avoid conflicts and ensure the correct values are used.

Roles are a fundamental concept in Ansible that enhance the scalability and maintainability of automation tasks by promoting modular and reusable code.

### Ansible with AWS

### Using AWS EC2 Instances with Ansible

To manage AWS EC2 instances with Ansible, you'll often use the following steps:

1. **Install Boto3**:
    - Ensure you have the `boto3` Python library installed, as it is required for Ansible to interact with AWS.
2. **Set Up AWS Credentials**:
    - Make sure your AWS credentials are configured. You can do this by setting up the `~/.aws/credentials` file or using environment variables (`AWS_ACCESS_KEY_ID`, `AWS_SECRET_ACCESS_KEY`, etc.).
3. **Use Ansible Modules for AWS**:
    - Ansible provides several modules to interact with AWS services, like `ec2`, `ec2_instance_facts`, `ec2_vpc`, and more. These modules allow you to create, modify, and delete AWS resources.
4. **Specify AWS Regions**:
    - Most AWS modules require you to specify the region where you want to perform actions, as shown in the `region: us-east-1` in the example.
5. **Using Dynamic Inventory**:
    - For managing multiple EC2 instances, you can use dynamic inventory scripts that fetch EC2 instance details and dynamically create an inventory of hosts. This is especially useful in large-scale environments.

### Clarifying `hosts: localhost` with AWS EC2:

1. **What Happens with `localhost`:**
    - When you specify `hosts: localhost`, you are telling Ansible to execute the playbook on the machine where Ansible is installed (e.g., your local machine or a control server). This does not mean that EC2 instances are running on your local machine. Instead, your local machine is **communicating with AWS services** via API calls.
2. **AWS API Calls vs. SSH:**
    - **AWS API Calls:** When interacting with AWS, you're often using APIs provided by AWS (via the `boto3` library) to manage resources like EC2 instances, S3 buckets, etc. These API calls can be made from your local machine to AWS without needing to SSH into the EC2 instances.
    - **SSH:** When you need to configure or manage an EC2 instance (e.g., installing software or running commands on the instance), you typically SSH into that instance. However, using `hosts: localhost` is not for managing the EC2 instances directly but rather for **interacting with AWS services** from your local machine.
3. **Example Use Case - Gathering EC2 Information:**
    - You want to gather information about running EC2 instances in a specific region. In this case, your playbook communicates with AWS to retrieve that information, but it does not directly connect to any EC2 instances. The playbook runs on your local machine, interacts with AWS using API calls, and fetches the data.
    
    ```yaml
    ---
    - name: Get EC2 Instance Details
      hosts: localhost
      gather_facts: false
      tasks:
        - name: Get facts about EC2 instance details
          ec2_instance_facts:
            region: us-east-1
            filters:
              instance-state-name: "running"
          register: ec2_details
    
        - name: Show EC2 instance details
          debug:
            var: ec2_details
    ```
    
    In this case, the `ec2_instance_facts` module interacts with AWS via API calls to fetch information about EC2 instances. The playbook itself runs locally on your machine (`localhost`) and does not SSH into the EC2 instances.
    
4. **When Do You Use SSH with EC2 Instances?**
    - If you want to run commands on EC2 instances, install packages, or configure the instances, you would need to SSH into the instances. In that case, you would not use `localhost`; instead, you'd specify the EC2 instance as a host, and Ansible would SSH into it.
    
    Example:
    
    ```yaml
    ---
    - name: Configure EC2 instances
      hosts: ec2
      become: yes
      tasks:
        - name: Install Apache
          yum:
            name: httpd
            state: present
    ```
    
    Here, `hosts: ec2` refers to your EC2 instances, and Ansible would SSH into them to install Apache.
    

### Summary:

- **`hosts: localhost`**: Playbook runs on your local machine and interacts with AWS via API calls (no SSH involved).
- **When managing EC2 instances directly**: You would specify the EC2 instances as hosts and SSH into them to perform configurations or tasks.

- **Using `localhost`**: Your local machine is managing or interacting with AWS (e.g., EC2 instances) via API calls using tools like Boto3, AWS CLI, or Ansible modules. You don't need to SSH into the instances in this case—you're just retrieving or managing data directly from AWS.
- **Using SSH**: This is when you need to connect directly to the EC2 instances to execute commands, configure services, or manage the system as if you were logged into the server. Ansible connects to these instances using SSH to run the necessary tasks

When using AWS with Ansible, you can automate the provisioning, configuration, and management of AWS resources (like EC2 instances, RDS databases, S3 buckets, etc.) by leveraging various Ansible modules designed to interact with AWS. Here’s an overview of how this integration works:

### **Key Components**

- **AWS SDK/CLI/Boto3**: Ansible uses the AWS SDK (via the Boto3 Python library) to interact with AWS services.
- **Ansible AWS Modules**: Modules like `ec2`, `s3`, and `rds` are designed to manage specific AWS resources. These modules allow you to define and automate your AWS infrastructure in playbooks.
- **IAM Credentials**: To interact with AWS, you need to authenticate using your AWS credentials, usually through environment variables, a credentials file, or AWS roles.

### **Setup Steps**

> First create an ec2 instance with required inbound permissions 
Download the pem file into the master machine and give the correct perm
( This is also available in the instances —> Connect —> ssh Client )
then ssh to your ec2 machine using the key then use sudo to create a new user for example aadmin (Commands that i used )
`adduser aadmin` 
`passwd aadmin` 
`usermod -aG wheel aadmin` # To add the user to the wheel group
Now create the .ssh in the user’s home directory and make’s its owner the new user
with 700 permissions for the .ssh directory 
`chown -R aadmin:aadmin .ssh`
now make a authorized_keys file and paste your master machine’s id_rsa.pub in here
and give it 600 permissions 
Then add the new user entry in the visudo `aadmin ALL=(ALL) NOPASSWD: ALL` 
Now add the ip and the user in the /etc/ansible/hosts file (the inventory file) 
`[aws]
13.53.193.107 ansible_user=aadmin`
Now check the connection 
`ansible aws -m ping`
> 

1. **Install Ansible**: Make sure Ansible is installed on your local machine or control node.
2. **Install Boto3 and Botocore**: These Python libraries are required by Ansible to interact with AWS.
    
    `pip install boto3 botocore`
    
3. **Configure AWS Credentials**: You can configure AWS credentials using one of the following methods:
    - **Environment variables**: Set `AWS_ACCESS_KEY_ID` and `AWS_SECRET_ACCESS_KEY`.
    - **Credentials file**: Located in `~/.aws/credentials`.
    - **IAM Role**: If running Ansible from an EC2 instance, you can assign an IAM role to the instance.
4. **Install AWS CLI** (optional but recommended): This allows you to test your AWS access from the command line and make quick API calls.
    
    ```
    pip install awscli
    aws configure
    ```
    

### **Using Ansible with AWS Modules**

### **Example: Provisioning EC2 Instances**

This example playbook demonstrates how to create an EC2 instance using Ansible:

```yaml
---
- name: Launch EC2 Instance
  hosts: localhost
  connection: local
  gather_facts: false

  tasks:
    - name: Create an EC2 instance
      ec2:
        key_name: my_keypair
        instance_type: t2.micro
        image: ami-0c55b159cbfafe1f0
        region: us-east-1
        wait: yes
        count: 1
        vpc_subnet_id: subnet-12345
        assign_public_ip: yes
        security_group: default
      register: ec2

    - name: Add new EC2 instance to the host group
      add_host:
        hostname: "{{ item.public_ip }}"
        groupname: launched
      with_items: "{{ ec2.instances }}"

    - name: Wait for SSH to come up
      wait_for:
        host: "{{ item.public_ip }}"
        port: 22
        delay: 60
        timeout: 320
        state: started
      with_items: "{{ ec2.instances }}"

    - name: Execute a command on the new EC2 instance
      hosts: launched
      tasks:
        - name: Ping the instance
          ping: 
```

### **Key Concepts:**

- **`ec2` module**: This is used to create EC2 instances. You specify parameters like the key pair, instance type, AMI ID, and region.
- **`add_host` module**: This dynamically adds the newly launched instance to the inventory group `launched` so that subsequent tasks can act on it.
- **`wait_for` module**: This ensures that the EC2 instance is ready for SSH access.
- **`ping` module**: This checks connectivity to the EC2 instance.

### **Managing EC2 Instances**

You can also use Ansible to manage existing EC2 instances, such as stopping, starting, or terminating them:

```yaml
---
- name: Manage EC2 instances
  hosts: localhost
  gather_facts: false
  tasks:
    - name: Stop an EC2 instance
      ec2:
        instance_ids: i-1234567890abcdef0
        state: stopped
        region: us-east-1
```

### **Dynamic Inventory with AWS**

In a dynamic environment, your EC2 instances may come and go, and you may not want to hardcode IP addresses or hostnames in your Ansible inventory. Instead, you can use Ansible’s AWS dynamic inventory feature:

1. **Install the AWS Dynamic Inventory Plugin**:
    
    ```bash
    pip install boto boto3
    ```
    
2. **Configure `aws_ec2` Plugin** in `ansible.cfg`:
    
    ```
    [inventory]
    enable_plugins = aws_ec2
    ```
    
3. **Create an `aws_ec2.yaml` inventory file**:
    
    ```yaml
    plugin: aws_ec2
    regions:
      - us-east-1
    filters:
      instance-state-name: running
    keyed_groups:
      - key: tags.Name
        prefix: aws_ec2
    ```
    

This setup allows Ansible to dynamically retrieve the list of running EC2 instances in the specified region(s), filtering by specific criteria like tags.

### **Best Practices**

- **Use IAM roles**: If running Ansible from an EC2 instance, assign the necessary IAM role to the instance instead of hardcoding credentials.
- **Leverage dynamic inventory**: It simplifies inventory management when dealing with cloud infrastructure.
- **Modular playbooks**: Break down your playbooks into smaller, reusable roles for managing AWS resources.
- **Test with `-check` mode**: This simulates playbook execution, which is especially useful when dealing with cloud resources to avoid accidental changes.