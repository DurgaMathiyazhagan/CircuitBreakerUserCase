# CircuitBreakerUserCase
Start the application using:
bash
Copy
Edit
mvn spring-boot:run
Access the endpoint:
url
Copy
Edit
http://localhost:8080/api/products/details
Since the external service is simulated to fail 50% of the time, the circuit breaker will:
Initially be in Closed State and allow requests.
Transition to Open State after failures exceed the threshold (50%).
Stay in Open State for 5 seconds (configured in application.properties).
Transition to Half-Open State and allow a few test requests.
If successful, move back to Closed State; otherwise, return to Open State.
Observe Fallbacks: When the circuit breaker is in the Open or Half-Open State, the response will be:
json
Copy
Edit
{
  "message": "Default Product Details (Fallback Response)"
}
