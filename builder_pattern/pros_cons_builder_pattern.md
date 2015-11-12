# Pros Cons Builder Pattern

**Advantages:**

1. More maintainable if number of fields required to create object is more than 4 or 5.

2. Less error-prone as user will know what they are passing because of explicit method call.

3. More robust as only fully constructed object will be available to client.

**Disadvantages:**

1. Verbose and code duplication as Builder needs to copy all fields from Original or Item class.
