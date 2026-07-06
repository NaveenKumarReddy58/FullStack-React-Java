

<h5>Since your Spring Boot application is created successfully, the next step is not Docker or AWS yet. Build it layer by layer.</h5>

<h5>Here's the roadmap I recommend for you.</h5>

<h3>Create your first REST API</h3>

<p>Create a controller.</p>
<code>
    @RestController
    public class HelloController {

        @GetMapping("/hello")
        public String hello() {
            return "Hello Spring Boot";
        }
    }
</code>