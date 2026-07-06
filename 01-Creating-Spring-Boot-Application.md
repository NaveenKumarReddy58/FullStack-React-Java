<h1>🌱 Creating a Spring Boot Application</h1>

<p>
This document explains how to create a Spring Boot application and why dependencies are required.
</p>

<hr>

<h2>📌 Objective</h2>

<ul>
    <li>Learn how to create a Spring Boot application.</li>
    <li>Understand the purpose of dependencies.</li>
</ul>

<hr>

<details open>
<summary><h2>🚀 Creating a Spring Boot Project</h2></summary>

<h3>Step 1</h3>

<p>
Open the official Spring Initializr website.
</p>

<a href="https://start.spring.io" target="_blank">
https://start.spring.io
</a>

<br><br>

<h3>Step 2</h3>

Choose the following configuration:

<table>
<tr>
<th>Option</th>
<th>Value</th>
</tr>

<tr>
<td>Project</td>
<td>Maven</td>
</tr>

<tr>
<td>Language</td>
<td>Java</td>
</tr>

<tr>
<td>Spring Boot</td>
<td>Latest Stable Version</td>
</tr>

<tr>
<td>Group</td>
<td>com.example</td>
</tr>

<tr>
<td>Artifact</td>
<td>demo</td>
</tr>

<tr>
<td>Packaging</td>
<td>Jar</td>
</tr>

<tr>
<td>Java Version</td>
<td>21</td>
</tr>

</table>

<br>

<h3>Step 3</h3>

Initially I added only:

<ul>
<li>Spring Boot Starter</li>
</ul>

<b>Result</b>

<ul>
<li>Application started successfully.</li>
<li>Application exited immediately.</li>
</ul>

<b>Reason</b>

<p>
No web server was available because the Spring Web dependency was not added.
</p>

</details>

<hr>

<details open>

<summary><h2>📦 What are Dependencies?</h2></summary>

<p>

Dependencies are external libraries that provide additional functionality to an application.

Instead of implementing everything from scratch, we include dependencies that already contain the required functionality.

</p>

<b>Examples</b>

<ul>

<li>Web APIs</li>

<li>Database Access</li>

<li>Security</li>

<li>Validation</li>

<li>Testing</li>

</ul>

</details>

<hr>

<details open>

<summary><h2>🌐 Spring Web Dependency</h2></summary>

<h3>Maven Dependency</h3>

```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-web</artifactId>
</dependency>
```

<h3>Purpose</h3>

<p>
Used to build REST APIs and web applications.
</p>

<h3>What it Provides</h3>

<ul>

<li>Embedded Tomcat Server</li>

<li>REST API Support</li>

<li>@RestController</li>

<li>@GetMapping</li>

<li>@PostMapping</li>

<li>@PutMapping</li>

<li>@DeleteMapping</li>

<li>Automatic JSON Conversion</li>

<li>DispatcherServlet</li>

</ul>

</details>

<hr>

<details open>

<summary><h2>❌ What Happens Without Spring Web?</h2></summary>

The application:

<ul>

<li>Starts successfully.</li>

<li>Executes the <code>main()</code> method.</li>

<li>Does not start Tomcat.</li>

<li>Does not listen on any port.</li>

<li>Exits immediately.</li>

</ul>

<b>Console Output</b>

```text
Process finished with exit code 0
```

</details>

<hr>

<details open>

<summary><h2>🔌 Default Port</h2></summary>

Default Port:

```text
8080
```

To change the port:

```properties
server.port=9090
```

</details>

<hr>

<details open>

<summary><h2>🔍 How to Know Which Port Spring Boot is Running On?</h2></summary>

Look for this log message:

```text
Tomcat started on port 8080 (http)
```

If this message is missing, the application is probably not running as a web application.

</details>

<hr>

<details open>

<summary><h2>📚 Official Resources</h2></summary>

<ul>

<li>
<a href="https://start.spring.io" target="_blank">
Spring Initializr
</a>
</li>

<li>
<a href="https://docs.spring.io/spring-boot/reference/" target="_blank">
Spring Boot Documentation
</a>
</li>

</ul>

</details>

<hr>

<details open>

<summary><h2>✅ Key Learnings</h2></summary>

<ul>

<li>Spring Initializr is used to create Spring Boot projects.</li>

<li>Dependencies add functionality to an application.</li>

<li>Spring Web is required to build REST APIs.</li>

<li>Spring Web starts an embedded Tomcat server.</li>

<li>The default port is <b>8080</b>.</li>

<li>Without Spring Web, the application exits immediately after startup.</li>

<li>The running port can be changed using <code>server.port</code>.</li>

</ul>

</details>
