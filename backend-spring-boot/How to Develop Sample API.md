echo "## Create Your First REST API

To get started, create a simple controller in your Spring Boot application.

\`\`\`java
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RestController;

@RestController
public class HelloController {

    @GetMapping(\"/hello\")
    public String hello() {
        return \"Hello Spring Boot\";
    }
}
\`\`\`

### How it works
- **@RestController**: Marks this class as a REST controller so Spring Boot can handle HTTP requests.
- **@GetMapping(\"/hello\")**: Maps HTTP GET requests to \`/hello\` and returns the response.
- **Return value**: When you visit \`http://localhost:8080/hello\`, you’ll see \`Hello Spring Boot\`.
" > README.md
