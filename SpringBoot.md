# The difference in Redirect & Forward

## Redirect

It's a two-step process where the server sends a *302 status* and a *new location* to the client. The client then makes a *new request** to this location. The URL in the client's browser changes.

## Forward

It's a one-step process that happens entirely on the server side. The request is sent to another resource within the same application, and the client is unaware of this change. The URL in the client's browser remains the same.

## Controllers type

Certainly! When working with a *Spring Boot application* and using the `@RestController` annotation, you can achieve redirection, although it's a bit different from traditional controller-based approaches. Let me explain how you can handle redirects in a `@RestController`.

1. **Using `HttpServletResponse`**:
   - In a `@RestController`, you can't directly return a view or perform a redirect like you would in a regular Spring MVC controller. However, you can still achieve redirection by adding an `HttpServletResponse` parameter to your handler method.

   - Here's an example:

          import org.springframework.web.bind.annotation.RequestMapping;
          import org.springframework.web.bind.annotation.RestController;
          import javax.servlet.http.HttpServletResponse;
          import java.io.IOException;

          @RestController
          public class MyController {
              @RequestMapping("/redirect")
              void handleRedirect(HttpServletResponse response) throws IOException {
                  // Perform any necessary logic based on input parameters
                  // Redirect the client to another URL
                  response.sendRedirect("https://example.com/other-page");
              }
          }

   - When you access the `/redirect` endpoint, it will send an HTTP redirect (status code 302) to the client, directing them to the specified URL.

2. **Using `ResponseEntity`**:
   - To avoid direct dependencies on `HttpServletRequest` or `HttpServletResponse`, you can use a "pure Spring" approach by returning a `ResponseEntity`.
   - Here's an example:

     import org.springframework.http.HttpHeaders;
     import org.springframework.http.HttpStatus;
     import org.springframework.http.ResponseEntity;
     import org.springframework.web.bind.annotation.RequestMapping;
     import org.springframework.web.bind.annotation.RestController;
     import java.net.URI;

     @RestController
     public class AnotherController {

         @RequestMapping("/another-redirect")
         public ResponseEntity<Void> handleAnotherRedirect() {
             // Perform any necessary logic
             // Create headers for redirection
             HttpHeaders headers = new HttpHeaders();
             headers.setLocation(URI.create("https://example.com/another-page"));
             // Return a 302 (FOUND) status with the new location
             return new ResponseEntity<>(headers, HttpStatus.FOUND);
         }
     }

   - This approach allows you to return a `ResponseEntity` with the appropriate headers for redirection. The client will receive a 302 status code and be redirected to the specified URL.

Remember that in both cases, the client (browser or API consumer) will follow the redirection and load the target URL. Choose the approach that best fits your use case and requirements! 🚀

In Spring Boot, you can use different methods to forward and redirect HTTP requests.

*Redirecting:*
Redirecting is used when you want to navigate the user to a different URL. In Spring Boot, you can use the `RedirectView` class or the `redirect:` prefix to achieve this.

Here's an example using `RedirectView`:

@Controller
@RequestMapping("/")
public class RedirectController {
    @GetMapping("/redirectWithRedirectView")
    public RedirectView redirectWithUsingRedirectView(RedirectAttributes attributes) {
        attributes.addFlashAttribute("flashAttribute", "redirectWithRedirectView");
        attributes.addAttribute("attribute", "redirectWithRedirectView");
        return new RedirectView("redirectedUrl");
    }
}

In this example, `RedirectView` will trigger an `HttpServletResponse.sendRedirect()`, which will perform the actual redirect¹.

You can also use the `redirect:` prefix:

@Controller
public class MyController {
    @GetMapping("/redirect")
    public String handleRequest() {
        return "redirect:/new-url";
    }
}

In this case, the `redirect:` prefix tells Spring to send a redirect response to the client¹.

*Forwarding:*
Forwarding is used when you want to forward the request from one controller to another within the same application. It happens entirely on the server side, and the client (browser) is not involved.

Here's an example:
@Controller
public class MyController {
    @GetMapping("/forward")
    public String handleRequest() {
        return "forward:/new-url";
    }
}

In this case, the `forward:` prefix tells Spring to forward the request to another URL within the same application¹.

**Remember**, when you want to return a view or redirect URL, you should use `@Controller` instead of `@RestController`². The `@RestController` annotation is designed to simplify the creation of RESTful web services and automatically serializes the response to JSON, which is not what you want when you're trying to return a view or redirect URL

## Spring boot

### Spring boot security

1. When not configured any security spring boot gives id pass
userName: user
password: after line "Using generated security password" 26746860-8ed6-4def-b4a2-c4259dfb3832

2. Check application pda_backend
