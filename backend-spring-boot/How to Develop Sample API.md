<section>
  <h2>Spring Boot Roadmap</h2>
  <p>Since your Spring Boot application is created successfully, the next step is not Docker or AWS yet. Build it layer by layer.</p>

  <h2>Here's the roadmap I recommend for you.</h2>

  <article>
    <h3>Create your first REST API</h3>
    <p>Create a controller:</p>

    <figure>
      <pre><code class="language-java">
        @RestController
        public class HelloController {

            @GetMapping("/hello")
            public String hello() {
                return "Hello Spring Boot";
            }
        }
      </code></pre>
      <figcaption>Java code for a simple REST controller</figcaption>
    </figure>

    <p>When you run the application and visit 
      <a href="http://localhost:8080/hello" target="_blank">http://localhost:8080/hello</a>, 
      you’ll see the message: <strong>Hello Spring Boot</strong>.
    </p>
  </article>
</section>
