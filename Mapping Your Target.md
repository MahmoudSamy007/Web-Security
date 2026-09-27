Mapping Your Target
Before finding bugs in application, first understand what it is about

### Application Mapping

- What is the goal of this app
- Target user category - is it for public usage or for internal usage
- Use all functions in the app with proxy configured to log requests history
- Check different roles
- Map all inputs
- What is the technology used in backend/frontend/web server/operating system
- Does it use a framework for client side or not?
- Quick check on headers - are there weird headers? Is there caching system? Can headers help fingerprint app
- Check cookies, auth headers, local storage
- Quick check on console - are there errors?
- What caught your eyes while exploring you want to focus on later?