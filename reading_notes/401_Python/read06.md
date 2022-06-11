# Reading 06 
> How to use Random Module
- The random module provides access to functions that support many operations. Perhaps the most important thing is that it allows you to generate random numbers.
- We want the computer to pick a random number in a given range Pick a random element from a list, pick a random card from a deck, flip a coin etc.
  - > Random functions 
    - Randint : 
      - to generate integer number from start point to the end point
    - Choice : 
      -  Generate a random value from the sequence sequence.
    - Shuffle:
      - shuffles the elements in list in place, so they are in a random order.
    - Randrange:
      - Generate a randomly selected element from range(start, stop, step)
    - getstate():
      - Return an object capturing the current internal state of the generator. This object can be passed to setstate() to restore the state.
    setstate(state):
      - state should have been obtained from a previous call to getstate(), and setstate() restores the internal state of the generator to what it was at the time getstate() was called.
    randbytes(number):
      - Generate n random bytes.
    getrandbits(k):
      - Returns a non-negative Python integer with k random bits
    sample(population, k, *, counts=None):
      - Return a k length list of unique elements chosen from the population sequence or set.
    uniform(a, b):
      - Return a random floating point number N such that a <= N <= b for a <= b and b <= N <= a for b < a.
    triangular(low, high, mod):
      - Return a random floating point number N such that low <= N <= high and with the specified mode between those bounds.
    - betavariate(alpha, beta):
      - Beta distribution. Conditions on the parameters are alpha > 0 and beta > 0. Returned values range between 0 and 1.
    - expovariate(lambd):
      - Exponential distribution. lambd is 1.0 divided by the desired mean.
    - gammavariate(alpha, beta):
      - Gamma distribution. (Not the gamma function!) Conditions on the parameters are alpha > 0 and beta > 0.
    - gauss(mu, sigma):
    - lognormvariate(mu, sigma):
    - normalvariate(mu, sigma):
    - vonmisesvariate(mu, kappa):
    - paretovariate(alpha):
    - weibullvariate(alpha, beta):
    - SystemRandom([seed]):


> What is Risk Analysis 
- risk analysis is the process of identifying the risks in applications or software that you built and prioritizing them to test. After that, the process of assigning the level of risk is done. The categorization of the risks takes place, hence, the impact of the risk is calculated.
  - Why use Risk Analysis?
    - using risk analysis at the beginning of a project highlights the potential problem areas. After knowing about the risk areas, it helps the developers and managers to mitigate the risks.
  - Risk Identification:
    - Business Risks: This risk is the most common risk associated with our topic. It is the risk that may come from your company or your customer, not from your project.
    - Testing Risks: You should be well acquainted with the platform you are working on, along with the software testing tools being used.
    - Premature Release Risk: a fair amount of knowledge to analyze the risk associated with releasing unsatisfactory or untested software is required
    - Software Risks: You should be well versed with the risks associated with the software development process. 
  - Risk Assessment :
    - In the risk analysis process, these steps prove to be the most important one. It is said that this step is way too complex and should be tackled with the utmost care. After risk identification, assessment has to be dealt programmatically.
      - The perspective of Risk Assessment:
        - Effect – To assess risk by Effect. In case you identify a condition, event or action and try to determine its impact.
        - Cause – To assess risk by Cause is opposite of by Effect. Initialize scanning the problem and reach to the point that could be the most probable reason behind that.
        - Likelihood – To assess risk by Likelihood is to say that there is a probability that a requirement won’t be satisfied.
  - How to perform Risk Analysis?
    - Searching the risk
    - Analyzing the impact of each individual risk
    - Measures for the risk identified

> TestCoverage (also called code coverage)
- they should aim for, or stating their coverage levels with pride.
- Test coverage is a useful tool for finding untested parts of a codebase. Test coverage is of little use as a numeric statement of how good your tests are.
- Sufficiency of testing is much more complicated attribute than coverage can answer. I would say you are doing enough testing if the following is true:
  - You rarely get bugs that escape into production, and
  - You are rarely hesitant to change some code for fear it will cause production bugs.



> Dependency Injection:
- transferring the task of creating the object to someone else and directly using the dependency
  - There are basically three types of dependency injection:
    - constructor injection: the dependencies are provided through a class constructor.
    - setter injection: the client exposes a setter method that the injector uses to inject the dependency.
  - Inversion of control —the concept behind DI:
    - Benefits of using DI:
      - Helps in Unit testing.
      - Boiler plate code is reduced, as initializing of dependencies is done by the injector component.
      - Extending the application becomes easier.
      - Helps to enable loose coupling, which is important in application programming.
    - Disadvantages of DI:
      - It’s a bit complex to learn, and if overused can lead to management issues and other problems.
      - Many compile time errors are pushed to run-time.
      - Dependency injection frameworks are implemented with reflection or dynamic programming. This can hinder use of IDE automation, such as “find references”, “show call hierarchy” and safe refactoring.

_____________________________THE END _______________THANK YOU FOR READING __________________________________________________________________________________________________
    

