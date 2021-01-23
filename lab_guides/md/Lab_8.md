

<img align="right" src="./logo.png">


Lab 8. Monitoring and Management of Tomcat 8
---------------------------------------------------------


Monitoring plays a vital role in an IT administrator\'s life. It makes
the life of a web/infrastructure engineer predictable. When I started my
career in web infrastructure support, I always wondered, how does my
boss know that a process is 90 percent utilized for a particular system
or how does he know that a particular process will die after about 90
minutes from now, without logging into the application? Later, I found
out that they have set up a monitoring system using various third-party
tools available in the market for servers and application
monitoring.

In this lab, we will discuss:

- How to monitor Tomcat 8
- Management of applications using the Tomcat Manager
- A third-party utility used for monitoring Tomcat 8


Before we learn how to monitor Tomcat 8, let us understand why
monitoring is actually required for any system, as we have configured
the systems well for the user.

The answer to this question is very tricky. In a real-time environment,
the system may break down due to many reasons such as a network glitch,
sudden CPU spike, JVM crash, and so on. There are some
revenue-generating applications, for example, if bank sites go down,
then there will be a huge revenue loss, also administrators will not
know unless users start complaining about the issues. This will also
have a bad impact on the business. If monitoring systems were set up on
the server, the web administrator would get a notification stating that
the following systems are going down, and he/she would take the
necessary actions to fix the problem. Hence, it minimizes the impact on
the application downtime.


### Note


IT administrators support thousand of servers, it\'s practically
impossible to validate the system every day. Hence, monitoring is very
helpful.


Different ways of monitoring
----------------------------------------------


In today\'s world, with increasing infrastructure, it becomes very
difficult for administrators to manage servers. In order to identify the
issue beforehand, and to minimize the downtime, monitors are configured
on the system. We can configure multi-level monitoring on the systems,
based on the infrastructure requirements for example, the OS, Web,
Application, and Database level servers and individual application
level. There are different ways of configuring multi-level monitoring.
The following figure shows different ways to configure monitoring for
any infrastructure:

![](./images/44.PNG)

Monitoring can be mainly done in three ways on a system, which are as
follows:

- **Third-party tools**

- Monitoring setups are configured using third-party tools present
        in the market, such as Wily, SiteScope, Nagios, and so
        on.
- These kind of monitoring tools are used in an enterprise
        infrastructure setup, where there are more than 100 servers with
        different infrastructure components (domains) such as web,
        application, database, filesystem servers, and so on.

- **Scripts**

- Scripts are used in monitoring, where a specific use case needs
        to be monitored, such as the results of how many users are
        logged in for a particular interval of time or
        application-specific user roles.
- Used everywhere in small and big IT organizations.

- **Manual**

- This process is used when any application\'s performance is slow
        for a particular module.
- Mostly used at the time of troubleshooting and where the number
        of systems are less than three.
    




Monitoring setup for a web application and database server
----------------------------------------------------------------------------



In the previous section, we have discussed the types of monitors, but
still we don\'t know which monitors are configured on these systems.
Let\'s prepare a table for the different infrastructure system monitors
and why they are configured. The following table shows the basic
monitors, which are normally configured for web application and database
servers:

![](./images/18.PNG)

Tomcat Manager in Tomcat 8
--------------------------------------------



The Tomcat Manager is a default tool for managing operations of Apache
Tomcat 8. It provides freedom to the IT administrators to remotely
manage the application and monitor the systems. Following are the
advantages of the Tomcat Manager:

- Allow remote deploy, rollback, start, and stop features for the
    administrator.
- Provide detailed monitoring status for the application and server.
- Administrators need not stay in the office 24x7. In case of any
    issues, he/she can log in to the Tomcat Manager to resolve the
    issue. In short, we can say remote administration of Tomcat becomes
    very easy for administrators.



### Note


It\'s not recommended to open the Tomcat Manager from the Internet. In
case you have to do so, then we have to enforce strong security policies
on Tomcat 8 or we can configure the **Virtual Private Network** (**VPN**) for the administrators.


Perform the following steps to access Tomcat Manager:



1.  You can access the Tomcat Manager using the URL
    http://localhost:8080/. The following screenshot shows the main page
    for Tomcat 8 with Manager App highlighted.

2.  Click on Manager App, it will prompt for the username and password.
    Provide the credential given in tomcat\_user.xml, where
    tomcat\_user.xml can be found in TOMCAT\_HOME/CONF.


![](./images/39.PNG)

3.  The Tomcat Manager console is displayed. If you look at the console,
    it gives you the complete picture of the application\'s deployment,
    server status, diagnostics, server information, and so on. The
    following screenshot shows the application\'s status and the
    different deployment-related tasks performed during application
    support:

 ![](./images/40.PNG)

The following screenshot shows the other features of the Tomcat 8
Manager such as:

- Deployment of a new application
- Diagnostic (memory or connection leak)
- Server information



-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
![](data:image/jpeg;base64,/9j/4AAQSkZJRgABAQEASABIAAD/2wBDAAgGBgcGBQgHBwcJCQgKDBQNDAsLDBkSEw8UHRofHh0aHBwgJC4nICIsIxwcKDcpLDAxNDQ0Hyc5PTgyPC4zNDL/2wBDAQkJCQwLDBgNDRgyIRwhMjIyMjIyMjIyMjIyMjIyMjIyMjIyMjIyMjIyMjIyMjIyMjIyMjIyMjIyMjIyMjIyMjL/wAARCADNAfQDASIAAhEBAxEB/8QAGwABAAIDAQEAAAAAAAAAAAAAAAUGAwQHAQL/xABNEAABAgMDBwgIAwUHAgYDAAABAAIDBBEFIVQSExQxkpPRBhVBUVNVkdIWFyIkUmGU4jJx4Qc2QmOBIzNic3SxslahNENEovDxJSbB/8QAGgEBAQEBAQEBAAAAAAAAAAAAAAECAwUEBv/EADERAAECAwYFAwMFAQEAAAAAAAABAgMUUQQTFVKRoRESYeHwBUHRITKBMTNCcbEiYv/aAAwDAQACEQMRAD8AnZO2bMk7PkoUxZljNc+G1jHR4YyohAAqT0nV4qR06Wyf3fsbcfoq2zk/HtKWlYucitgOlhBexkEuymlwcaO6K5IBuOparOQkwyMKTExkCrw8wCXl5Iv+Ro0VPTfqX591of8AX/vh+OJ60VqI9f7qvyWyHaUnFhtiQ7CsZ7HCrXNg1BHXqX1p0r/0/Y+5/RVZ3IyYZRsu+MGviNy3GE5rhDFaioHtEhxaCaUarEJOO1oDZeIABQAQ3UA8F88W1WhvDkdx/CGWo1f146qZ9Olf+n7G3H6Jp0r/ANP2NuP0WHRJjsIu7dwTRJjsIu7dwXzz1s8RDXIyq6mfTpXuCx9z+iadK9wWPuf0WDRJjsIu7dwTRJjsIu7dwVnrZ4iDlZVdVM2nSv8A0/Y+5/RNOlf+n7H3P6LDokx2EXdu4Jokx2EXdu4JO2zxEHKyq6qZtOlf+n7G3H6Jp0r/ANP2NuP0WHRJjsIu7dwTRJjsIu7dwUnrZ4iDkZVdTPp0r3BY+5/ReadK9wWPuf0WHRJjsIu7dwTRJjsIu7dwSetniJ8DlZVdVM2nSvcFj7g8E06V7gsfcHgsOiTHYRd27gmiTHYRd27gk9bPET4LyMquqmbTpXuCx9weCadK9wWPuDwWHRJjsIu7dwTRJjsIu7dwSetniIORlV1UzadK9wWPuDwTTpXuCx9weCw6JMdhF3buCaJMdhF3buCT1s8RByMquqmbTpXuCx9weCadK9wWPuDwWHRJjsIu7dwTRJjsIu7dwSetniIORlV1UzadK9wWPuDwTTpXuCx9weCw6JMdhF3buCaJMdhF3buCT1s8RByMquqmbTpXuCx9weCadK9wWPuDwWHRJjsIu7dwTRJjsIu7dwSetniIORlV1UzadK9wWPuDwTTpXuCx9weCw6JMdhF3buCaJMdhF3buCT1s8RByMquqmbTpXuCx9weCadK9wWPuDwWHRJjsIu7dwTRJjsIu7dwSetniIORlV1UzadK9wWPuDwTTpXuCx9weCw6JMdhF3buCaJMdhF3buCT1s8RByMquqmbTpXuCx9weCadK9wWPuDwWHRJjsIu7dwTRJjsIu7dwSetniIORlV1UzadK9wWPuDwTTpXuCx9weCw6JMdhF3buCaJMdhF3buCT1s8RByMquqmbTpXuCx9weCadK9wWPuDwWHRJjsIu7dwTRJjsIu7dwSetniIORlV1UzadK9wWPuDwTTpXuCx9weCw6JMdhF3buCaJMdhF3buCT1s8RByMquqmbTpXuCx9weCadK9wWPuDwWHRJjsIu7dwTRJjsIu7dwSetniIORlV1UzadK9wWPuDwTTpXuCx9weCw6JMdhF3buCaJMdhF3buCT1s8RByMquqmbTpXuCx9weCadK9wWPuDwWHRJjsIu7dwTRJjsIu7dwSetniIORlV1UzadK9wWPuDwTTpXuCx9weCw6JMdhF3buCaJMdhF3buCT1s8RByMquqmbTpXuCx9weCadK9wWPuDwWHRJjsIu7dwTRJjsIu7dwSetniIORlV1UzadK9wWPuDwTTpXuCx9weCw6JMdhF3buCaJMdhF3buCT1s8RByMquqmbTpXuCx9weCadK9wWPuDwWHRJjsIu7dwTRJjsIu7dwSetniIORlV1UzadK9wWPuDwTTpXuCx9weCw6JMdhF3buCaJMdhF3buCT1s8RByMquqmbTpXuCx9weCadK9wWPuDwWHRJjsIu7dwTRJjsIu7dwSetniIORlV1UzadK9wWPuDwTTpXuCx9weCw6JMdhF3buCaJMdhF3buCT1s8RByMquqmbTpXuCx9weCadK9wWPuDwWHRJjsIu7dwTRJjsIu7dwSetniIORlV1UqnKqPCfakJzbPkoIMEezCg+z+J16L45UwojLShB0KI05kXZB+JyL6G2mNw+qnrQ2t5E+u5b7Pl7YdZMhFs2PDYBKsyRFi0ZlAxMoFnTWrKHop47FOVUaIQY0qwQXtoSQ0RP7O+lNYyia1uqBS4Ky8kJKUi8lLOfElYL3mCKudDBJvPTRTvNslg5fdN4L1ksPFOPFNO5+ejRuERycPdSjyz+UToc8yM+Wy2Nh6O6gAcTe6/UaC6tKVPUFqy8vyqgS4Zpko9wyKmI/LJu9o1P5DxPSuhc2SODl903gnNkjg5fdN4JI9U0Od/wBChubynz4c2ZlMmlHNJbkg5RvF1aUydd9AelZJV/KEtnIceLLGIyDDzL8kNa6Ib3gHpDaUBprdfqV55skcHL7pvBObJHBy+6bwUX09F9007i/6FFiy1vTFmvZEnYMKbMw3JMF4aBCyQ114F7r3H8wKUWk2z+UxAy7QhXtyHe8m6r8rKuA1ABtxBoXLo/Nkjg5fdN4JzbI4OX3TeCrbCqfyTTuFj8fY57M2fygiQJMQbQDIjJUw43vFxiVd7QNL/wCGhP8Avetl0PlDEkGkzEm2cbMl4yHUYYWS4UPXeQb/AJV1K882yWDl903gnNsjg5fdN4JIf+k07i/6FCf6UZoZEWRzucbeXNycjprdXK66XdSwGDysfKOgvnJTK9gB7Xhr9V5rSmvXd+S6HzZI4OX3TeCc2yODl903giWHh7poL/oUqd9IXT0YyUaSbL5ysMPIrk0uHjr/AOy+Zv0kNoRzKR5EShec1nKZWTkigP8AWt+vV0C+782SODl903gvebJHBy+6bwUT09Kpp3F/0KK9vKdr2hk3IOYDSrwAT7INT0fiJF3UD0kKaly9srCbHitdGDG5xwIALqX6vnVT/Nkjg5fdN4JzZI4OX3TeCy705HJw5tipaOHsQuW34m+ITLb8TfELdjtsuWmYcJ8nDL31NGQAcloIBc664VIv/VYdN5OlzW5cgS8VFGtN1Cam664HWueEpn27mproYMtvxN8QmW34m+IWzpFg5YYGyb3mG6JksY1xyWgEm4dRC12WnyezAiOhy0IuNAx8JocdWoDX+IeKuFJn27kmuh5lt+JviEy2/E3xC2mx7CdBgRw2UzUcVhvLG0Ooa6XXkD819CY5Pu/C6zycjLAGRe3rTCkz7dyzXQ08tvxN8QmW34m+IWxEnOTsKC+I50hRgqQAwnXTUPnctqDLWdNS7YsvKy5a40qYIu67qJhSZ9u4muhG5bfib4hMtvxN8QpbmuXw0n9OOKc1y+Gk/pxxTCUzbdyTXQictvxN8QmW34m+IUtzXL4aT+nHFOa5fDSf044phKZtu4muhE5bfib4hMtvxN8QpbmuXw0n9OOKc1y+Gk/pxxTCUzbdxNdCJy2/E3xCZbfib4hS3NcvhpP6ccV9Ns2SLfak5Yn5Qm8FMJTPsJroQ+W34m+ITLb8TfEKa5skcHL7pvBObJHBy+6bwTCUz7Ca6ELlt+JviEy2/E3xCmubJHBy+6bwTmyRwcvum8FcJTPsJroQuW34m+ITLb8TfEKa5skcHL7pvBObJHBy+6bwTCkzbCa6ELlt+JviEy2/E3xCmubJHBy+6bwTmyRwcvum8EwpM2wmuhC5bfib4hMtvxN8QprmyRwcvum8E5skcHL7pvBMKTNsJroQuW34m+ITLb8TfEKa5skcHL7pvBObJHBy+6bwTCkzbCa6ELlt+JviEy2/E3xCmubJHBy+6bwTmyRwcvum8FMKTNsWa6ELlt+JviEy2/E3xCmubJHBy+6bwTmyRwcvum8EwpM2wmuhC5bfib4hMtvxN8QprmyRwcvum8E5skcHL7pvBMJTPsSa6ELlt+JviEy2/E3xCmubJHBy+6bwTmyRwcvum8FcJTPsJroQuW34m+ITLb8TfEKa5skcHL7pvBObJHBy+6bwTCkzbCa6ELlt+JviEy2/E3xCmubJHBy+6bwTmyRwcvum8EwpM2wmuhC5bfib4hMtvxN8QprmyRwcvum8E5skcHL7pvBMKTNsJroQuW34m+ITLb8TfEKa5skcHL7pvBObJHBy+6bwTCkzbCa6ELlt+JviEy2/E3xCmubJLBy+6bwTmySwcvum8EwpM2wmuhx/l4Rz9C9r/wBO3p/xORZ/2lSsuzlJBayBBA0Vt2bHxvRZw9KnoMjryodD5F/ufZv+SP8Acqw9Kr3Iv9z7M/yR/uVYelewz7UPJjfuO/tT1ERaOYREQBERAEREAREQBERAF5UDpXqg7ckZ2fhsZJzBgey8PIiOYTUUFKaqH2q/4adJQG7NWfKzj2ujwcstBb+IioNKg0N4uFxuuWr6O2W5hY6VDgcqtXuJNRQ1Nb6jrWtZcja8tOR4k3MMjMjt1tiuIhECgo0j5D+tVhh2fb0NkKHAmocEf+a50UxS511XDKaaV1gC4X1rW4CShWJZ8F5dCl8klpY6j3XimTQ333AD+g6l5GsCy474MSLKisFmRDo5zQ0fIA0UKyW5TScwyGyYbHzsV0WI8kZI62kltRW4ADV81sRJLlREiQa2hL5sAmIAQMp1TQfg1Up+fyQEsbGkniE0wRkQ8qjK3HKoTX+oWr6M2UYjHZhwYxmQGCI4N6L9eu6h6+mqxy8pbwiHPz0HN5LhksArUg0NcnoOTTqGuqw2ZZluyhZBjz8J8DNua68udlZIDTUj5V8eu6A3Tyesp1+iNBDQyrXOBoCbqg/Mj8jTUt6BAhyMu2EwuyWmtXVJJJv/AN1XYtjW3FLownGMeGNa2GI79Ybkkh2oVNCbjX5G9WaEYubDozclxNS0OygP60CoGlN+ew7gmlN+ew7gs2W3rCZbesIDDpTfnsO4JpTfnsO4LNlt6wmW3rCAw6U357DuCaU357DuCzZbesJlt6wgMOlN+ew7gssMgsBBqDevctvWF4z8P9T/ALoD7REQBERAEREAREQBERAEREAREQBERAEREAREQBERAEREAREQBERAEREByH9pn7zwv9K3/k5E/aZ+88L/AErf+TkXBT1YX2IXzkX+59mf5I/3KsPSq9yL/c+zP8kf7lWHpXVn2oedG/cd/anqIi0cwiIgCIiAIiIAiIgCIiAIiICNta0XWdLMitgGMXvzbWh1CXEHJH9TQf1UO/lfBq0Qpdz8sNMM1dRxLqAXNJrkkPoKmnQrQWtdSoBpfevjMwwAAxtAagU1HrQEMOUUq3Q2xGRBFm4cN7GNo6mWaAVr+d/y/ILE7lNCgzRgzECgMRzGGE/LJyXll4oMk1Ffyr1KdzEEFpEJlWigOSLl4IEFpLmwmAuOUSGipPX+aAgmcrZCJDZGhtjuhONC4tDcn2XO1E1P4ejrHzWaW5Qy02CyE2NlUcWhzKB2SKuoanUaCvWRrqpbRJev9xC1U/ANX/wleNlIDYzYrYTQ9rMhpApRt1w8B4BAV2LyvZCikNlA+GGMcXiLd7TMqlcml14vI1XVNysYeIzKscQK0ymkX/kgloAZmxCZkH+HJFNddS+IphSsAZEPJaCAGw2jWbhdqQGbM/zYm0mZ/mxNpaune1k5mPlUrT2K0/Kq+tNPYTHg3igNjM/zYm0mZ/mxNpa+muA/uJjwbxWeFEEaG2IxxyXAOFR0FAe5n+bE2kzP82JtL7ofiKUPxFAfGZ/mxNpMz/NibS+6H4ilD8RQHxmf5sTaTM/zYm0vuh+IpQ/EUB8Zn+bE2kzP82JtL7ofiKUPxFAfGZ/mxNpewxRtKk0JvK+qH4ivWjJCA9REQBERAEREAREQBERAEREAREQBERAEREAREQBERAEREByH9pn7zwv9K3/k5E/aZ+88L/St/wCTkXBT1YX2IXzkWf8A9Qsz/JH+5U/UdK5ZZ/KUWRY1nS8SJPVdLNe1sFzA2hLgKVHxBrfzeFvQ+V8GLMwoEOanXOiTDoApFh6w5jQRdfXLBHTQFcUtjUThwU+ONCW8cvH3U6NUJX5rnLuV8tCm4sCYm5+CIcV8Ivc5pqWktuAbW8ggLdicoJWFNNl32pOtc6HDiNdT2S1+o1yfyrXVUItuYnsuhi5WpebkuVBi8qJOXtCJJxbUnGPYQ3KNCHOq4ED2egtNTqXwzlZIPiubzpPBoY1+UW9Br0ZNRQAG/wCIJPNouguVqdCqEqOtVCSnhaMq2ZlLSm4kFxIa8OABoaGlW9a2qTOPm9tvlXNfUYSLwVFNS7iyVC9qq17zj5vbb5U95x83tt8qmJQeol3llqlVWvecfN7bfKnvOPm9tvlTEoPUS7yy1SqrXvOPm9tvlT3nHze23ypiUHqJd5ZapVVr3nHze23yp7zj5vbb5UxKD1Eu8stUqq17zj5vbb5U95x83tt8qYlB6iXeWWqVVa95x83tt8qe84+b22+VMSg9RLvLLVKqte84+b22+VPecfN7bfKmJQeol3llqtK0WvdLf2TS57XtdRuu4hQ/vOPm9tvlT3nHze23ypiUHqJd5Gz1kT03NxI8J0WA97W5MRsGsRha1zRR1dXtXj5LWbYlsOeTFnpslrgWGjzWjKX+1d/EPZoaE311TfvGPm9tvlT3jHze23yq4lB6iXeatnS1qyj4+kRJuODkiHlAmgDbz/V1f6UCs8o0slILHCjmw2gjqNFBe84+b22+VPecfN7bfKpiUHqJd5ZapVVr3nHze23yp7zj5vbb5UxKD1Eu8stUqq17zj5vbb5U95x83tt8qYlB6iXeWWqVVa95x83tt8qe84+b22+VMSg9RLvLLVKqtVmcfN7bfKlZnHze23ypiUHqJd5ZapVVr3nHze23yp7zj5vbb5UxKD1Eu8stUqq17zj5vbb5U95x83tt8qYlB6iXeWWqVVa95x83tt8qe84+b22+VMSg9RLvLLVKqte84+b22+VPecfN7bfKmJQeol3llqlVWvecfN7bfKnvOPm9tvlTEoPUS7yy1SqrXvOPm9tvlT3nHze23ypiUHqJd5ZapVVr3nHze23yp7zj5vbb5UxKD1Eu8stUqq17zj5vbb5U95x83tt8qYlB6iXeWWqVVa95x83tt8qe84+b22+VMSg9RLvLLVKqte84+b22+VPecfN7bfKmJQeol3llqlVWvecfN7bfKnvOPm9tvlTEoPUS7yy1SqrXvOPm9tvlT3nHze23ypiUHqJd5ZaryqrfvOPm9tvlT3nHze23ypiUHqJdxRv2m/vPC/0rf+TkWhy8MTn6FWYik6O29zxX8TvkizPwup6kKAvIhdOTVjmc5NWdGLZNwMABudgl7gMqtK16wD+YHUpUcnT0Ms8XAXSx1Agjp6CAR+QX3yL/AHQsz/JH+5Vg1r6m2aGqcVQ8qNEdeOTj7qVx/JvOFxfDs9xdXKJlia111v8AmV6/k++JEbEeyQc9lMlzpYktpqoa9FSrIisrCoYvX1Ky/k5lve90OQL3nKc/RjlE6q1rWt5vXxB5LMl4MGFBhSDGwQ0Q6Sxq3J1Gta1vN/zVoRWWh0F6+pXpSwI0jKQpWXiSzIMJuSxubeaDaWfmmcxEtuneZTSLK2SCq8VaL19SG5pnMRLbp3mTmqdxEtuneZTSKSUHKL59SF5pnMRLbp3mXnNU5iJbdO8ym1qTrYzpGO2Xc5sUsIYWkVBpdSt3iklByi+fUj+apvES27d5k5qnMRLbp3mUbTlQyGGw2QCIbasMSIC559q515+V1TqHtG9bkHnuPFc2Yc2Ex0OI2sINo15DchwNSfi1jX8qFWSg5RfPqZua5vES27d5k5rm8TLbt3mUcIPKb2XZ2HlZTYha6IKfE6HcOs5IPUNa+WS3KFtmFgjPEznob6mICC3J9oVN49rX0dVxSSg5S3z6knzVOYiW3TvMnNM5iJbdO8y1YbuUYlTliXzrIwDQCDlw8g/iJPxU6jrXs3NW/Dk4L4UtDfEMP28kAlrqkasqlaEajStb6JJQcpL59TZ5qnMRLbp3mXjrNmmCrpqVA6zDd5lHB/KmHCcWwJWJEJBq54pe6pvrWlLvkKUrepiydOEsXWlQRnRXEAUoG9AFCUkoOUXz6mroMbGSew7zJoMbGSew7zKdqOtKjrSSgZRfPqQWgxsZJ7DvMmgxsZJ7DvMp2o60qOtJKBlF8+pBaDGxknsO8yaDGxknsO8ynajrSo60koGUXz6kFoMbGSew7zJoMbGSew7zKdqOtKjrSSgZRfPqQWgxsZJ7DvMmgxsZJ7DvMp2o60qOv/uklByi+fUgtBjYyT2HeZNBjYyT2HeZTtR1pd1/90koOUt8+pBaDGxknsO8y+HSzmEh1oyII1gg+ZWDKb1jxVXtObjslZ2DJxMiOYpLSHAH8QJ1kdFekJJQMovn1NjMHvGQ8D5k0c4+Q8D5lBw7V5RQoLGgysRwB/vHtqaAUyjlazfqr8+sjbPKYMP9nIZZDbg8UBqa/wAV91D0Ur0lJKBlF9EqTjZZznBrbQkSSaAAG87Sz80zmIlt07zLWNpGYh5DgGlzmjJLgT+IdRKsiSUHKS+fUheaZzES26d5k5pnMRLbp3mU0iklByi+fUheaZzES26d5k5pnMRLbp3mU0iSUHKL59SF5pnMRLbp3mTmmcxEtuneZTSJJQcovn1IXmmcxEtuneZOaZzES26d5lNIklByi+fUheapzES26d5k5qnMRLbp3mU0iSUDKL59SE5pnMRLbp3mXvNM5iJbdO8ymkSSg5RfPqQvNM5iJbdO8yc0zmIlt07zKaRJKDlF8+pC80zmIlt07zJzTOYiW3TvMppEkoOUXz6kLzTOYiW3TvMnNM5iJbdO8ymkSSg5RfPqQnNM7iJbdO8y95pnMRLbp3mU0iSUHKL59SF5pnMRLbp3mTmmcxEtuneZTSJJQcovn1IXmmcxEtuneZec0zmIlt07zKbRJKDlF8+pxb9oEpHh8oIQdEhOOjNvax1PxO/xItr9pn7zwv8ASt/5PRYlodD0mRXcqF95F/ufZv8Akj/cqwdKrPJCblofJGzWRJiE1wgiodEAOs/NTvOEnioG8bxX2M+1DzY37jv7U20WrzhJ4qBvG8U5wk8VA3jeK0czaRavOEnioG8bxTnCTxUDeN4oDaRavOEnioG8bxTnCTxUDeN4oDaRavOEnioG8bxTnCTxUDeN4oDaRavOEnioG8bxTnCTxUDeN4oDaolFq84SeKgbxvFOcJPFQN43igNqiUWrzhJ4qBvG8U5wk8VA3jeKA2qJRavOEnioG8bxTnCTxUDeN4oDaotOajPgw4YbkAvfk1eKgXE6rupfXOEnioG8bxWpPxZaagtayelmOa4Oq54I1EdfzQGrEtyHBjxIUaZhQhDOSYj4JDK5IdTKytdCCjrflGvyTaciaEgkMJDaDpOUo6YsOz5p0R0eak4hiXuDohpWgFQMqgPsi8X3LEzk5ZjQazUoTlEtOedVlTWjaOuH5ICdbaJiwoj4E1KRc20khjCeg/4vkVLNIc0GmsVVVlrLlpRkaHBn5NojPc91HDWQBqrqAAH9FYGz0m1oGlwLhT+8bxQG5RKLV5wk8VA3jeKc4SeKgbxvFAbVEotXnCTxUDeN4pzhJ4qBvG8UBtUSi1ecJPFQN43inOEnioG8bxQG1RKLV5wk8VA3jeKc4SeKgbxvFAbVF8GGxxqWNJ+YWDnCTxUDeN4pzhJ4qBvG8UBmzUPs27ITNQ+zbshYecJPFQN43inOEnioG8bxQGcQ2A1DGg/kvtavOEnioG8bxTnCTxUDeN4oDaRavOEnioG8bxTnCTxUDeN4oDaRavOEnioG8bxTnCTxUDeN4oDaRavOEnioG8bxTnCTxUDeN4oDaRavOEnioG8bxTnCTxUDeN4oDaRavOEnioG8bxTnCTxUDeN4oDaRavOEnioG8bxTnCTxUDeN4oDaRavOEnioG8bxTnCTxUDeN4oDaRavOEnioG8bxTnCTxUDeN4oDaRavOEnioG8bxTnCTxUDeN4oDaRavOEnioG8bxTnCTxUDeN4oDaRavOEnioG8bxTnCTxUDeN4oDaRavOEnioG8bxTnCTxUDeN4oDlf7TP3nhf6Vv/JyLF+0qYgP5SwXNjQSNFbflj43ouCnqwvsQ6Nycgy55N2YTDhE6LCrVo+AKUzUt2cLZC4PGtQSEGUhMhyz3mXzr2xT7b/ba0NZTW41PXqWP0rkWlzTJh7g3KBa5gF94BqfZuvv1r4Z+Jw/5Zx/J88WzIj3cXe533NS3ZQtkLzNS3ZQtkLg7uUsoyEXus57RSrcpzGh34q3nV+BwFdZFAvmJyokxEiw4UjUsfkVe5gr7JNaa+ilNdepE9QiL/BdUMS6ZjvealuyhbITMy/ZQtkLhUtyglJiYkoIkwHTTyxpD2HJp0kA1B13axRTuZhdmzZC4xfVlhLwezh+TTbJzfo46xmpbsoWyEzUt2ULZC5PmYXZs2QmZhdmzZC5443Jv2NSS1OsZqW7KFshM1LdlC2QuT5mF2bNkJmYXZs2QmOtyb9hJLU6xmpbsoWyEzUt2ULZC5PmYXZs2QmZhdmzZCY43Lv2EktTrGaluyhbITNS3ZQtkLk+ZhdmzZCZmF2bNkJjjcm/YSS1OsZqW7KFshM1LdlC2QuT5mF2bNkJmYXZs2Qpjjcu4klqdYzUt2ULZCZqW7KFshcnzMLs2bITMwuzZshXHG5d+wklqdYzUt2ULZCZqW7KFshcnzMLs2bITMwuzZshMdbk37CSWp1jNS3ZQtkJmpbsoWyFyfMwuzZshMzC7NmyExxuXfsJJanWM1LdlC2QmaluyhbIXJ8zC7NmyEzMLs2bITHW5N+wklqdYzUt2ULZCZqW7KFshcnzMLs2bITMwuzZshMdbk37CSWp1jNS3ZQtkJmpbsoWyFyfMwuzZshMzC7NmyEx1uTfsJJanWM1LdlC2QmaluyhbIXJ8zC7NmyEzMLs2bITHG5N+wklqdYzUt2ULZCZqW7KFshcnzMLs2bITMwuzZshTHG5dxJLU6xmpbsoWyEzUt2ULZC5PmYXZs2QmZhdmzZCuONyb9hJLU6xmpbsoWyEzUt2ULZC5PmYXZs2QmZhdmzZCY43Jv2EktTrGaluyhbITNS3ZQtkLk+ZhdmzZCZmF2bNkJjjcm/YSS1OsZqW7KFshM1LdlC2QuT5mF2bNkJmYXZs2QmONyb9hJLU6xmpbsoWyEzUt2ULZC5PmYXZs2QmZhdmzZCY43Jv2EktTrGaluyhbITNS3ZQtkLk+ZhdmzZCZmF2bNkJjjcm/YSS1OsZqW7KFshM1LdlC2QuT5mF2bNkJmYXZs2QmONyb9hJLU6xmpbsoWyEzUt2ULZC5PmYXZs2QmZhdmzZCmONy7iSWp1jNS3ZQtkJmpbsoWyFyfMwuzZshMzC7NmyFccbk37CSWp1jNS3ZQtkJmpbsoWyFyfMwuzZshMzC7NmyExxuTfsJJanWM1LdlC2QmaluyhbIXJ8zC7NmyEzMLs2bITHG5N+wklqdYzUt2ULZCZqW7KFshcnzMLs2bITMwuzZshMcbk37CSWp1jNS3ZQtkJmpbsoWyFyfMwuzZshMzC7NmyExxuTfsJJanWM1LdlC2QmaluyhbIXJ8zC7NmyEzMLs2bITHG5N+wklqdYzUt2ULZCZqW7KFshcnzMLs2bITMwuzZshMcbk37CSWp8ftLZCHKWCAxlNFb0D43oq7yghwxaDAGMpmh0fMotYpx/ietDsbuRPqWiz5ez4djS0xMRnNLJYRohbLl+abeKk9FaFbU1YdgzsLNzE9JRmVa7Jdk9P4dTvBb9gWKJ/k5JRXSrYjYksGOOkFmW2poHAa6Emletb0LkjAgRWxYVlwoUTKDstk04EHVrA6RcetRbK9V5kavH8HmRoqc7k4+6kKyWsd8tLxuc4DYUw0uhF7AA4NoTrNxFRd0LNEsyy4T6RLTlmuIbE9oNBIdcHa+noKlW8koLJSXlWWZCZBlyXQWsmnDNk0JoQLrwD+d6R+R8CYiQnxbJgOMKG2HD94IDWt1ACn9PySSfx/T/AAzfpUhZmUsqTlHzkS0YWZhOc1z4cMOyHUJIuOu4rZ5skspzHWlDa9kMRHscAHNadRIyrgpL0ShCTdKCyZcS74mcLBMEDKoR1dRKyv5NF83MTT7OhOjTEIwYrjMn2mEAEUpQahq6lhbC5f47IL9KkDGg2TAgvivtiAWsaXENo40GugDqlZYkjZ0JsN0S1oDGxGl7C4tAc0ayPavAW8ORMm1uS2xpdooW3TLgaH50/wDpezvI2DPQYcKJINaYUMw4T2TRymA1qRUXm83musphy5dkJfpX/SJjMsmC2ptaG+8CkNoeRUFwqAbrgV9xZeyYLcqJbMu0XjovoaH+K+8hSTeRcu10Zz7NZEESIXZL5kkNq0NNLumlT0k/0X2/kdAiOhvdZrC6EMmHWcf7AvuHVSpp1KyC5dkLfpUimS1lva13O8FuVk0a7JBqRUCmVrTRbMzsaE61YTIkCKIMRrwGlrzSgvPTW5Sw5GywDQLIgUaKNGlOu66XdPT1r6muR8KdjRI0xZcF8SI/LedKcKn+gUw9eP2bIL9KkYLPkDDhxBasEw4tc272aPprp7V9F8CUstwYRbMsQ+gaQ5vtVpSntfMeKlxyWbo7IAs9jYbQ8ANm3C55q4EgXgkA0+QWAch5QNDRZEDJAAppTqXEHq+Q8FE9Odl2QX6V/wBI5kpZsSYgQIVqQ4sSPlZtsNodXJBJ1G7UV66TsxkBsd1sS4gucWNeS3JLhrAOVrClZXkpBko0OJL2ZBhvhtLWkTLtRBF4pfc4j5Ar1nJGFDlWSzbLg5pkQxGtM040caVNaV6B4Ivp7uP2bIS/Sv8ApEOlrKYKutqWAu1ub0io/i6l6ZSywQDbMteQB7TdZFR/F0hSbeRcsz8Njy4vBumXax/RfD+RcF8B8NlmwoZdDfCDmzJJYHNLXUBBF4J/rerhy5dkF+lf9I90nZzIzYT7Uhtc9jXsJaA1wcSBQ1oakFeQZSzY80ZaDakOJFyC+jQDcCQb66wReOhS8XkrDjaMYtlwHmWhthwiY59lra0Gr5n86r5leSECSj5+XsuAyLkuYXGZcSWu/EDUXg3eA6lMPdw+3ZBfpX/SNhSFnR3hkK1oER5aXhrS0ktGs/i1XHwWFkKyIhdkW1LHJ1mrafhyteV1Gqm5bkrDlYwjQbMgtigUyzNOJpQt6R1Ej8lqxeQ8o6ViQGWayGHsLKtm3Ei6lbxSouIr0gKp6evH7NkF+lf9NY2ZJiXZMG04WZeQ1kSgyXE6gDlLDDl7Mixc2y1oRd7NDQUdlVoAcq8+yVNt5NES+jukGPgh+cDHzJcA6hBN46cok9ZJWEci5UNDRZMCgaG/+KdeK1obrxW/+g6lE9Pd7t2QX6VIuHK2ZFjwYMK1IUV8VrnszYDhkt1kkG79CvuHIWdFa50O1oD2taHOLckgAmgJ9rpNykpbkjAlYlYNlwWnJew1mnEODq5VQRfWpFVkh8lWQoExBZZ0IMmA0RfenEvyTVtTStRXWi+nu9m7IL9KkHGg2TBhPiOtiCWsLQQyjjU6hQOrevYsCyoLHPda8F2SCaMo4mhoaAOqb1K+hkrkgc0waAU/8U7V1atX+6+G8iJdsbKFmQs3m8gQtJOQLya0prvp8hqWk9O/87IL/qacKzpCPEzcG1IMR9SMlmSTdXoyvkfBbHo8zEnd/qtqW5K6HaMOdl5KG2JDhOhNAmK3Oya3ltdTWgDUApXQbQw0Lf8A2rk/0+Jx/wCWf4aSO33UgfR5mJO7/VPR5mJO7/VT2g2hhoW/+1NBtDDQt/8Aas4fHyJsW/ZUgfR5mJO7/VPR5mJO7/VT2g2hhoW/+1NBtDDQt/8AamHx8ibC/ZUgfR5mJO7/AFT0eZiTu/1U9oNoYaFv/tTQbQw0Lf8A2ph8fImwv2VIH0eZiTu/1T0eZiTu/wBVPaDaGGhb/wC1NBtDDQt/9qYfHyJsL9lSB9HmYk7v9U9HmYk7v9VPaDaGGhb/AO1NBtDDQt/9qYfHyJsL9lSB9HmYk7v9U9HmYk7v9VPaDaGGhb/7U0G0MNC3/wBqYfHyJsL9lSB9HmYk7v8AVPR5mJO7/VT2g2hhoW/+1NBtDDQt/wDamHx8ibC/ZUgPR5mJO7/Ve+jzMSd3+qntBtDDQt/9qaDaGGhb/wC1MPj5E2F+ypA+jzMSd3+qejzMSd3+qntBtDDQt/8Aamg2hhoW/wDtTD4+RNhfsqQPo8zEnd/qno8zEnd/qp7QbQw0Lf8A2poNoYaFv/tTD4+RNhfsqQPo8zEnd/qno8zEnd/qp7QbQw0Lf/amg2hhoW/+1MPj5E2F+ypA+jzMSd3+qejzMSd3+qntBtDDQt/9qaDaGGhb/wC1MPj5E2F+ypA+jzMSd3+qejzMSd3+qntBtDDQt/8Aamg2hhoW/wDtTD4+RNhfsqQHo8zEnd/qvfR5mJO7/VT2g2hhoW/+1NBtDDQt/wDamHx8ibC/ZUgfR5mJO7/VPR5mJO7/AFU9oNoYaFv/ALU0G0MNC3/2ph8fImwv2VIH0eZiTu/1T0eZiTu/1U9oNoYaFv8A7U0G0MNC3/2ph8fImwv2VORctbNEvbUKHnC73dprkf4nfNFJcvpeYbb8IPhMa7R23Z7/ABO+SLpKRU9j1YUZORPqXrk+5jeSViZbA9uad7JFRqKwRp+cgRYz22XBjsMdzITBDAyWAXOJDa3/APyi2uTkGYHJWzIMSRhx2tgNe0mMBrFerqKlNEd3NB3w4L9Cz7UPzsb9x39qVx1sTmTGjtsJpDHtDYOa9otyX1qaX0IbqqL6C9eOt2bM1DY3k7SEMkxHFlaAtNei+hpqqrLoju5oO/HBNEd3NB344LRzNCz5ts3Ly0WJItlI7orasDaFvt010BvH+6tCh2S74b2vbZEEOaag58XHwW1pM/gG78cEBvItHSZ/AN344JpM/gG78cEBo2rFtWBNNfJNzkIMBdCMO4nLAPtC8eySf6LDDtW0HS8059lRWRITGPhhwccsuN4uHRroKn+qlNIn8A3fjgmkT+AbvxwQFcfyotOTl2umrIiA5DSXuymAvJ/CBQ3no/7rbNt2s1vtWHEygASGlx/iGr2eo6usdV6lzGnXUrZ7DS/+/HBBMT4/9A3fjggI2StS0oxDJuznsOQXVAcA5wH4RUUF93tG+t1Vr882xUvFjPiMfkZIblNLa0yq5Tfnrp0HovU3pE/gG78cE0ifwDd+OCAjpa1LSizDhEs97YZgF7SQ4UiAn2Lx03X6uomoWCWtW2Ju0JYPsqLKy7jSJltqQL769CmNIn8A3fjgvNIn8A3fjggK9F5R2nJy8GJNWVRz8loblOblvuqBUVB10rdQXlbdm29P2lFhtbZZZAe6mk5ZyCBlVIq3/CBf1/lWVMaddStnsNP544L0R55ooLPYB/njggIh1sWs+HCjtsuKxjZl7IsMscXuhhvsuApdUnq6Fi59tCTs9sxOSP8AaRJnNNh0LTkkCgAoSTWo6ruhTmkT+AbvxwXhizrjU2ew0/njggINlvWw4Q4rrEisYcsOh0eXEilD+G4a9eu/poD7Jcp5+anIUsbGe11WCOMs1g5VfxXfKv5a6Kd0ifpTQG78cF8iLOtNRZ7K/wCeOCAiZu1bVGcErZUTLynta7JcaUNx1AGov10vuJNQsYtq2nQnt5oeyI3U54cQ+lK3NF2snX8rzcpzSJ/AN344JpE/gG78cEBFy9s2k+O1kSx4gh5QD4hLqgXCtMm831u6PncvZ+0bTlYsVsCTiRww5TWiG6jmZA/iA15RN2u7+qk9In8A3fjgmkT+AbvxwQEW+1LVfKOissuJDiNmhCDH1dWH0vuFfBeT9rWvDm4kGBZMQshvAEY1c1zekgAV1HxCldIn8A3fjgmkT+AbvxwQEU21rUhysqYtlOfHfELIuSTRoya5VKVv6vkfksUO2rZc1znWJE/G0BlXAtBydZpQkEuvF1w6L1NaRP4Bu/HBNIn8A3fjggIqHa9rmagQ4ljPDIkQNL2vJDGnWTVv/wAofkkxbM/LR2th2NHitMV7XFgd7LRqd+Ghrrurr66qV0ifwDd+OCaRP4Bu/HBAQrbbtgVc6xori5xyWgOFBfQG7XShJ1dGu5bEa1LTY2XLLJe+LEYcsBzqMdlU15OrpvoaG7pUlpE/gG78cE0ifwDd+OCAio1t2g2bhwIFlPiuMFkSIMogwy4E0Ps0/hprrU6qLALbtdscF1jxzCzYo0B1S6txqW3Aiuu8fxUU3n56tdAbvxwTSJ/AN344ICHFs2swkmyHvYcnJDWvGsCtatrWtRq+ZuvWwbWtFktBiRLLLXvilj25ZoxuTUOJybh0EnVQqR0ifwDd+OC8MeeIoZBtP88cEBCvty04gZFlrHiOguhiK29xLgWOIGqgNQ2uvX10WSJbdsshuicxvIDQQ0PcXV/LJ+R8QpYR54CgkG78cF7pE/gG78cEBtQ35bA7JLa9BGpZFo6TP4Bu/HBNJn8A3fjggN5Fo6TP4Bu/HBNJn8A3fjggN5Fo6TP4Bu/HBNJn8A3fjggN5Fo6TP4Bu/HBNJn8A3fjggN5Fo6TP4Bu/HBNJn8A3fjggN5Fo6TP4Bu/HBNJn8A3fjggN5Fo6TP4Bu/HBNJn8A3fjggN5Fo6TP4Bu/HBNJn8A3fjggN5Fo6TP4Bu/HBNJn8A3fjggN5Fo6TP4Bu/HBNJn8A3fjggN5Fo6TP4Bu/HBNJn8A3fjggOX/tM/eeF/pW/8nIsH7SYsc8o4JiSzWu0Vt2eHxv+SLgp60L7ELZYfK2Tl7DkYJlJtxhQIbC5obQkNAP8XyUh6byODnPBnmXKolmzk4yyosDJDILQS58QgC8EnJGs0AoQR0g1BSDIcpGy2VEn2mYYA5jS8ZDnZQqHUb+GgNB/ip0LynW2Mn0RyJ/adTlEgQ+d30X9Tq3pxI4Oc8GeZPTeSwc54M8y5dAs+22z7hHtF75TOC8OAcWAHoybiTSvXescWzLaMeaiwZwws7Ee9rGxLqEOArd0AM1dZKxP2jjw5m6L8kl4dFOqnlvJDXJzvgzzJ6cSODnPBnmXJ5SybblG6PDnDo0O5n9rUuAyi2ns+zX2Q7WTeV5Es7lIyBEbCtF0R7hQOfFDcn5ijflq6jToWp20ceCOTRSS7KKdZ9N5LBzngzzJ6byWDnPBnmXJjZnKDOl7Z2hLiKmLeAXEg/h/CPZ9npprUrZsvaEF8Z07MGKH0LW1BDDVxIFwoKFo/pVYieoWhreKKi/hSts8NV4cFOhem8lg5vwZ5k9N5LBzfgzzKm0KUK+XF7VRNF+TcpCLp6byWDnPBnmT03ksHOeDPMqXQ9SUPUpi9pomiiUhVLp6byWDnPBnmT03ksHOeDPMqXQ9SUPUmL2qiaKJSFUunpvJYOc8GeZPTeSwc54M8ypdD1JQq4vaqJoolIVS5em8lg5zwZ5k9N5LBzfgzzKm0KUKuLWvKmi/IlIRcvTeSwc34M8yem8lg5vwZ5lTaFKFTFrVRNF+RKQi6em8lg5zwZ5k9N5LBzngzzKl0PUlD1FTF7VRNFEpCqXT03ksHOeDPMnpvJYOc8GeZUuhSh6kxe1UTRRKQql09N5LBzngzzJ6byWDnPBnmVLoepKHqTF7VRNFEpCqXT03ksHOeDPMnpvJYOc8GeZUuhShTF7VRNFEpCqXT03ksHOeDPMnpvJYOc8GeZUuhShVxe1UTRRKQql09N5LBzngzzJ6byWDnPBnmVLoUoVMXtNE0USkKpdPTeSwc54M8yem8lg5zwZ5lS6HqSh6kxe1UTRRKQql09N5LBzngzzJ6byWDnPBnmVLoepKHqKYvaqJoolIVS6em8lg5zwZ5k9N5LBzngzzKl0KUPUmL2qiaKJSFUunpvJYOc8GeZPTeSwc54M8ypdClCri9pomiiUhVLp6byWDnPBnmT03ksHOeDPMqXQpQpi9qomi/IlIVS6em8lg5zwZ5k9N5LBzngzzKl0PUlD1KYvaqJoolIVS6em8lg5zwZ5k9N5LBzngzzKl0PUlD1Ji9qomiiUhVLp6byWDnPBnmT03ksHOeDPMqXQpQpi9pomiiUhVLp6byWDnPBnmT03ksHOeDPMqXQpQq4vaqJoolIVS6em8lg5zwZ5k9N5LBzngzzKl0KUPUpjFpomiiUhVLp6byWDnPBnmT03ksHOeDPMqXQ9SUPUri9qomiiUhVLp6byWDnPBnmT03ksHOeDPMqXQ9SUKYvaaJovyJSFUunpvJYOc8GeZPTeSwc54M8ypdClCmL2qiaL8iUhVLp6byWDnPBnmT03ksHOeDPMqXQ9SUPUmL2qiaL8iUhVLp6byWDnPBnmT03ksHOeDPMqXQpQ9SmL2miaKJSFUjOXVqwLTt2FHZLx2gS7W0dk1/E4/F80URymutGF/kj/dyL6E9QjKnH6Hqw7IzkT6nRuTcvAfyckXPgwnOMIVLmAk3lS2iy2Hg7tvBYuSdmwZjkrZ0V8SOHOgiobFIGs9AU3zNA7WZ37l9DvToj15kd+p48W0NSI5OHupE6LLYeDu28E0WWw8Hdt4KX5kl+1md+5R1qQ5GyIEOLGiTRy4jYYAjH8yfyABP9FMLiZjnMtoRc3CgMihgEKETk0OQ3prW6nyHisOYg0HvcCv+Uxb3OVg55sETM6YryQxmU6rj0U/PoXspNWVNzMOVbEnWTMRz2thuiOvya311UNF6EKArGI1WovDyhwc/ivFFUjXw4cOXzmehOfrzYhsrrH/APFkdBly6jZqCACNcNhrW/q6qf1qtpk7IQ4Z0zSoUWrqMhxnRKgOLdYAv9lxp1BfUW0bFhSr5h8aeENjgx1XOByj/DTr1eK6XSZE8/BObqvn5NHMwcgETUCpFf7tnUOjxW7Ky0uYZqIMa8+3m2+C+4USVjPDmwpzMZh0dzzMnKAaASMn8zTXrBR0xJQpCXnIrZtsOKYjXkTVQwsDjrrfXJoKda4WiyrFZytRE8/o0yIjV4rxUy6LLYeDu28E0WWw8Hdt4LekZGVnZGBNNiTIbGhtiAaQTQEV1g0K2eZJftZnfuXxYXEzHeZbQiNFlsPB3beCwOlpfToIzEGhhPNMgdbVPcywO1md+5az7JgC0oEPOTF8GI7+9NbnM6f6qt9Men8iLaW0NHRZbDwd23gsMzLQGwHFkKAw1HtFjRQVv1hTvM0DtZnfuXxEseXawkPmnED8IjGpWofpz2uRyqikdaGqnDgVyHDknOvjMAN4uZcKgEG7Xr/7LCxsu8OrGhMIiFgqxmqtx1aqV/rRSMGLJxo0jDpNs0qXz/tRz7NxOTdcTceno6V42LLPsfnBrJgnLyBC0rWa3AHpJqLh03fNejdf+E8/Bw5uqmgIMGhrNQLv5bB18AsstLwTGAMaBF1+xm2X+Cym1LHEvpBiThhiNEhksjlxAbX2qA6jT87wtqzWQbRjZOamWNELLc4TZdkuyi3Ju11ySajqWIkDmYrUaicfKFa9EXiqqNFlsPB3beCwzUtLtk45ECCCITiCGC64qd5lgdrM79y1p+yYEKQmojYkwS2C8isUkfhPQvPT0x6Lx5jutpbQj2SstkN93g6h/wCW3q/JfWiy2Hg7tvBSrLFlzDac7M6h/wCe5fXMkv2szv3KYXEzCZbQiNFlsPB3beCaLLYeDu28FL8yS/azO/com0XSlmzEFkbSzCeCXxdIdRl9Bd/9f1NyYXEzFmW0MUaFKwYTojpVjg0VIZBDnf0AFSqq+ftxkKGeZIJLXwzFAlK5THitG9RbRwPzp1q0Rp6yxKzUaXdOx3S4BLRFc3Kq4NNCbjQlfMtaVlR88S+eAhl5BbGc7KYDc+7oN1Om8Loz06I1PqqKZW0NX2IPSrUhSsg99jQo0WNKiLHZDlwMiI0EvZfqyrg2vTXWvmPa88JaKYXJgtiZusNxh5TcqgN4Da0qadd19FYhPWLlhpmpttxNXPeAAKX/APcH8l8OtOxWxnQ3Rp9uSQ1xJfc4kClNdb66tQK1IP8AfhuS/Qj7Pm4k5O5iNYQloYa5xixGClQQA38Ou8nquuJUvosth4O7bwXxCnrGjRocIRp9rokQQ25bngEnVf1avELyDN2ZFmXSxiTojiI6HkiI4g0JBIOq4UJ/Nc3emRFXiiomppLQ2hk0WWw8Hdt4Josth4O7bwUuLFlyK52Z37k5kl+1md+5ZwuJmEy2hEaLLYeDu28FgjS0uJiVAgQQC51RkC/2Cp3mWB2szv3LVmbJgtnZNgiR6Pc+tYxr+E6lW+mPRfuC2ltDT0SWw8Hdt4Josth4O7bwUvzJL9rM79y8NiwADSJM1/z3KYXEzCZbQrtowxAlMuXlILnZxjXEQA8sYXAOdkgVNBU0UVDmbQMKZzllwRFEiYsJolbs6BcHV6TcQ0V6QaEXyjLVs8uGcbPMHT/blx6qADWcsOb+bSsjbVsZ0ZzDGngwNDg/LdQ1qD87iAD8yujPTnonDiikWO1V/Qr8O2LRbSFG5Ll8Ul9XNhZLRR+SP4TUEX1/7Lfs2eizk6yXmOTxlWGGXGK9oLQb7h7I+XipeDNWXOCKJKJOx4rILozWCI5uWBcQCemtywPtSymMc7OTjg4/2Wbik5xvQQdV99L+had6e5abkS0IbWiy2Hg7tvBNFlsPB3beC2rPgWdacOK+VmJpzYUV0J9YzhRw1/7hbvMkv2szv3Ljhb8xqZbQgZuWlxBbSBBH9rDFzB8Y+Sz6LLYeDu28Fuztky8OAw5yYNY0Jt8YnW9oWzzLA7WZ37lV9MfwROYTLaEBaEIQLPjxZWSgxY7GVYzNA1P5dP5dKjZWJNRbQhQYsjBEu8RAIolMnUXZD3V/CCALtdeihFLlzLA7WZ37l4bFl6H+1mt+5bb6c9qcOKGVjtVf0KDCtS0WQwY3JvOPLXXNhZFHMaAeg3F1SP8ADSlVl51mxMPa7k04sa4s9mFcSHEVByb6gClwF95U3FnJKHAm4gE2dHj5nJMyQTStXX6vwuprrQdanhYsAiudmb/57lqQctNxfoVuyniflDFmbKZJxA/Jzb2A1FAa6h10/MFb2iy2Hg7tvBS/MsDtZnfuTmWB2szv3LkvpsRV+ioamW0IFktL6dHBgQaBkOgyBd+L5LPosth4O7bwW5CsmA60ZlmcmKNZDpSMa35S2uZYHazO/cjvTHqv3BLQ2hE6LLYeDu28FXZmZtCHpRh2ZB/s3OIGiEkARKANOp5cz2q3AG4kK88ywO1md+5OZYHazO/ctM9OiNX6qikW0NX2KXNTk1AtYwoNhiNKljGtfmAP7QltSXX0Aa49GtpvWrEtO0S9xhcnmFjobHMAgmrX5Rymuq0VuoLtR1VCvpsWXAvizO/cq7O2rZstGMOG2djUL2OIjuFHg0yadN/6VW09Pf03JfoQ0O15yJLuJ5M5EUNNMphyXODK0oGVvOqt3WQV7zxNZtxHJhxLGkuORQE1Auqy/XX8gelXWWs2WmJaFHbFmcmIwOFJhxuIqsvMsDtZrfuTD3UTVRfoQkCBAiy8KI+ThQnvYHOhljSWkjVq6Fl0WWw8Hdt4KX5lgdrM79y85kgdrM79y4r6Y/MaS0toch5eQITbehBsOE0aO27IHxORbP7R5GHB5RQGCJFporT7UU1/G9FJB9T0GR05UOicmJacg8mLNbDmYAZo7CA6ASbxXXl/NTGbtDFS307vOua2R+0h0pZMhKiyg7IgMblaRStGi+mStv1rO7mH1P2L2EiIiIh8MWxR1eq8vuvuh0DN2hipb6d3nWN0tOuvdMShNCKmWPTr/jVD9a7u5h9T9ietd3cw+p+xL1piRj5d0Liyx83CEKGyzgwAimhVuN5/j6VsCRmWuDmxJEObWhEoaj/3qjetd3cw+p+xPWu7uYfU/Yl60SMfLuheDITBiZZfJF1KV0Q1pWtPx9d6+HWZFc7KdzeXXXmTvu1fx/M+KpXrXd3MPqfsT1ru7mH1P2JetEjHy7p8l5ZJTUNoDIsm0AUAEqRQVr8aQ5KZhMayHEk2tb+ENlSALqXe31Kjetd3cw+p+xPWu7uYfU/Yl60SMfLunyX1sCfY0NbMyoAFABLEU/8AevvN2hipb6d3nXP/AFru7mH1P2J613dzD6n7EvWiRj5d0OgZu0MVLfTu86wmVnjMsjmbl8trHMA0c0oSCf4/8IVF9a7u5h9T9ietd3cw+p+xL1okY+XdDoGbtDFS307vOmbtDEyv07vOuf8ArXd3MPqfsT1ru7mH1P2JetEjHy7oXnQZnKa7OSWUy5p0Q3atXt/IeCwGyHucC50oWDVCMu4wwddQzLya/OlVTfWu7uYfU/YnrXd3MPqfsS9aJGPl3QvT5OZiUyokk7JflisoTR3X+PX815ClJqA0NhRZOG0CgDJUi7+j/mqN613dzD6n7E9a7u5h9T9iXrRIx8u6HQM3aGJlvp3edYY8rPR5eJBfNS4bEaWGku6tCKfGqL613dzD6n7E9a7u5h9T9iXrRIx8u6fJf2wrQa0DSpa4U/8ADu869zdoYqW+nd51z/1ru7mH1P2J613dzD6n7EvWiRj5d0OgZu0MVLfTu86wRZKZjPa+JEk3vZUNc6VJIrrp7ao3rXd3MPqfsT1ru7mH1P2JetEjHy7oXlkhMQ2ZDHyLW0pRsoQKba+ObYxyamQ9n8Pueq6l3t9SpPrXd3MPqfsT1ru7mH1P2K3rRIx8u6fJc4llPjMc1+hZLq5VJUitTU3h/SdfX0r75ujFxOVI1JyidE1moNfx9YHgqT613dzD6n7E9a7u5h9T9iXrRIx8u6fJeNAjktdlyFWmrToZuPWPbXjrPjv/ABOkD7WVfKdOuv49apHrXd3MPqfsT1ru7mH1P2KXrRIx8u6F+EGfaAGzMqANQEs7zr6zdoYqW+nd51z/ANa7u5h9T9ietd3cw+p+xL1okY+XdDoGbtDEy307vOsESTnYseDFM3L5UIktpLnpFPjVG9a7u5h9T9ietd3cw+p+xL1okY+XdDoGbtDFS307vOmbtDFS307vOuf+td3cw+p+xPWu7uYfU/Yl60SMfLuheNBma3xJL6Q9dfj6yT/VfPNsXLyv/wAflVrXQ760p8fVcqT613dzD6n7E9a7u5h9T9iXrRIx8u6fJeWSMzDfnGRJJr6ZOU2VINK1p+PrXwbNjODQ4yBDRQVk9QpSn41SfWu7uYfU/YnrXd3MPqfsS9aJGPl3T5L1BlJqA0iDFk4bSakMlSBXrues2btDFS307vOuf+td3cw+p+xPWu7uYfU/Yl60SMfLuheo8pPR2NY6alwA9r7pc62kEfx/JZc3aGKlvp3edUD1ru7mH1P2J613dzD6n7EvWiRj5d0+ToGbtDEy307vOmbtDEy307vOuf8ArXd3MPqfsT1ru7mH1P2JetEjHy7oXd0hMOzmU+QOW4OdWUPtG68+3ebh4BbObtDFS307vOuf+td3cw+p+xPWu7uYfU/Yl60SMfLuh0DN2hiZb6d3nTN2hipb6d3nXP8A1ru7mH1P2J613dzD6n7EvWiRj5d0Ly2UnWTMSOJqXyogaD7u6l1afx/NZ83aGJlvp3edc/8AWu7uYfU/YnrXd3MPqfsS9aJGPl3Q6Bm7QxMt9O7zpm7QxMt9O7zrn/rXd3MPqfsT1ru7mH1P2JetEjHy7odAzdoYmV+nd51qus2K+9xkDcW3yfQbiPxqk+td3cw+p+xPWu7uYfU/Yl60SMfLuhfmwZ9rQ1szLAC4ASx86+s3aGKlvp3edc/9a7u5h9T9ietd3cw+p+xL1okY+XdDoGbtDFS307vOvM3aGKlvp3edUD1ru7mH1P2J613dzD6n7FbxokY+XdCG/aRDmfSOBlxoTnaK29sA0/G//Gir3LPla21rXgzL5DNnRw3JzuVqc7pyUXFXoenCssbkTsf/2Q==)
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------



Monitoring in Tomcat 8
----------------------------------------



Monitoring in Tomcat 8 can be done using the Tomcat Manager. By default,
the Tomcat Manager provides the status of the server with a detailed
description of requests and their status. This information is very
useful to administrators at the time of troubleshooting. Apart from
this, the administrator need not log in to the machine for collecting
this information. It takes a minimum of 30 minutes to collect the entire
information of the application, if you are checking the server status
manually, but using the Tomcat Manager, you are getting it online.
That\'s truly amazing and a great help for IT administrators.


Let\'s discuss the various components used for monitoring that are
available in the Tomcat Manager.



### Summary of the Server Status of Tomcat 8


The basic synopsis of Tomcat 8 includes the details of the JVM, HTTP,
and the HTTPS connection, which can be accessed using the
URL` http://localhost:8080/manager/status`. The following
screenshot shows the synopsis of Tomcat 8:


---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
![](data:image/jpeg;base64,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)
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


The displayed synopsis of Tomcat 8 contains the details of the JVM, HTTP
connection, and the AJP connection summary. The details of the output
summary for each component are as follows:

- JVM

- **Free memory** 
- **Used memory**
- **Total memory**

- Connections on the HTTP port

- **Max threads**
- **Current thread count**
- **Current thread busy**
- **Max processing time** (ms)
- **Processing time** (s)
- **Request count**
- **Error count**
- **Bytes received** (MB)
- **Bytes sent** (MB)

- Connections on the AJP

- **Max threads**
- **Current thread count**
- **Current thread busy**
- **Max processing time** (ms)
- **Processing time** (s)
- **Request count**
- **Error count**
- **Bytes received** (MB)
- **Bytes sent** (MB)
    

#### Complete Server Status of Tomcat 8


This page gives the complete report of Tomcat 8\'s status. It includes
all the parameters which are part of the **Server Status**.
In addition to that, it displays the detailed application list,
application response time, servlet response time, and so on. It can be
accessed using the
URL` http://localhost:8080/manager/status/all`. Let\'s discuss
each component of the dashboard briefly.



##### Application List


This gives us the list of all applications hosted in Tomcat 8 and their
URL mapping for the application\'s access. The following screenshot
shows the application list deployment in the Tomcat 8
instance:


----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
![](data:image/jpeg;base64,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)
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


The following points gives the details of the applications hosted in
Tomcat:

- **Application details:** Once we click on the
    application list, it displays the complete summary of the
    application including its internal deployment component. The
    following screenshot shows the internal components with their
    statuses such as the status of the application response, servlet
    response, and the JSP responses:



------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
![](data:image/jpeg;base64,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VSV9tNvN5iV045w2m3m8xLacc4sHZndjyr2pXzhszuv5V7Ur5wdbgYqkr7abebzErpxzhtNvN5iV045xYOzO6/lXtSvnDZpdfyr2pXzg63AxVJX20283mJXTjnDabebzErpxziwdmd1/KvalfOGzO7HlXtSvnB1uBiqSvtpt5vMSunHOG0283mJXTjnFg7M7seVe1K+cfdmd2PKP6hfODrcDFUle7TbzeYldOOcNpt5vMS2nHOLC2Z3Y8o/qF84bM7seUf1C+cHW4LiqSvdpt5vMSunHOG0283mJXTjnFhbM7seUf1C+cNmd2PKP6hfODrcExVJXu0283mJbTjnDabebzErpxziwtmd2PKP6hfOGzO7HlH9QvnB1uBiqSvdpt5vMSunHOG0283mJbTjnFhbM7seUf1C+cNmd2PKP6hfODrcFxVJXu0283mJXTjnDabebzErpxziwtmd2PKP6hfOGzO7HlH9QvnB1uBiqSvdpt5vMS2nHOG0283mJXTjnFhbM7seUf1C+cNmd2PKP6hfODrcExVJXu0283mJXTjnDabebzErpxziwtmd2PKP6hfOGzO7HlH9QvnB1uC4qkr3abebzErpxzhtNvN5iW045xYWzO7HlH9QvnDZndjyj+oXzg63BMVSV7tNvN5iV045w2m3m8xK6cc4sLZndjyj+oXzhszux5R/UL5wdbgYqkr3abebzEtpxzhtNvN5iW045xYWzO7HlH9QvnDZndjyj+oXzg63AxVJXu0283mJXTjnDabebzEtpxziwtmd2PKP6hfOGzO7HlH9QvnB1uC4qkr3abebzEtpxzhtNvN5iV045xYWzO7HlH9QvnDZndjyj+oXzg63BMVSV7tNvN5iV045w2m3m8xLacc4sLZndjyj+oXzhszux5R/UL5wdbgYqkr3abebzErpxzhtNvN5iV045xYWzO7HlH9QvnDZldjyr+oXzg63BcVSU3btv2jbs8manXGVOobDdUsClASf9zCO6v3YVm2FbzUrJtOpbVLpcI7RSsypQ3/wEI8qqh2baoxPgsmx7Om37KsqaZnlsJTIsIShNaVpVRPdup3d2+NoWbbuBI+aJCgpJriJyBNU5pzrln6Up3xTsnbVqtyss2i05xKOxb+0PqA3fisZ/ntr8VntQvnFpX4Q89z/m+9Xz/qlsIsq3wtKnbWSpKRkBU1Pd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)
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


- **Application response:** Application response for a
    deployed application gives us the current state of the application.
    For example, the previous screenshot shows the following parameters
    with reference to the current behavior of the sample
    application:

- **Start time**
- **Startup time** (ms)
- **TLD scan time** (ms)
- **Active sessions**
- **Session count**
- **Max active sessions**
- **Rejected session creations**
- **Expired sessions**
- **Longest session alive time** (s)
- **Average session alive time** (s)
- **Processing time** (ms)
- **JSPs loaded**
- **JSPs reloaded**

- **Servlet details:** In this section, the dashboard
    displays the response time of the servlet deployed for a sample
    application with the following parameters:

- **Processing time** (s)
- **Max time** (ms)
- **Request count**
- **Error count**
- **Load time** (ms)
- **Classloading time** (ms)

- **JSP:** In this section, the dashboard displays the
    response time of the JSP deployed for a sample application with the
    following parameters:

- **Processing time** (s)
- **Max time** (ms)
- **Request count**
- **Error count**
- **Load time** (ms)
- **Classloading time** (ms)



##### JVM


In this section, the dashboard displays the JVM memory utilization for
the Tomcat instance. The first column in the following screenshot shows
the JVM memory utilization for the sample application with the following
parameters:

- **Free memory**
- **Used memory**
- **Total memory**


##### Connections on the HTTP port (8080)


In this section, the dashboard displays the HTTP connection status for
the Tomcat instance. The second column in the following screenshot shows
the HTTP connection status for the application sample with the following
parameters:

- **Max threads**
- **Current thread count**
- **Current thread busy**
- **Max processing time** (ms)
- **Processing time** (s)
- **Request count**
- **Error count**
- **Bytes received** (MB)
- **Bytes sent** (MB)


##### Connections on the AJP


In this section, the dashboard displays the AJP connection status for
the Tomcat instance. The third column in the following screenshot shows
the status of AJP connection for the application sample with the
following parameters:

- **Max threads**
- **Current thread count**
- **Current thread busy**
- **Max processing time** (ms)
- **Processing time** (s)
- **Request count**
- **Error count**
- **Bytes received** (MB)
- **Bytes sent** (MB)



![](./images/38.PNG)


JConsole configuration on Tomcat 8
----------------------------------------------------



**JConsole** is one of the best monitoring utilities that
comes with JDK 1.5 or later. The full form of the JConsole is the[
**Java Monitoring and Management Console**. It\'s a graphical
tool, which gives complete details of the application and server
performance. It gives us the following information about the application
hosted in Tomcat 8:

- Detect low memory
- Enable or disable the GC and class loading verbose tracing
- Detect deadlocks
- Control the log level of any loggers in an application
- Access the OS resources---Sun\'s platform extension
- Manage an application\'s **Managed Beans**
    (**MBeans**)




### How to connect to the JConsole


Once Tomcat 8 configurations are done, it\'s time to connect to Tomcat 8
through the JConsole remotely using the command` jconsole`, as
follows. It will open the GUI interface. We have to provide the IP
address and port for the server where we want to connect; in our case,
it\'s` localhost` and` 8086`. The following
screenshot shows the default console for the JConsole:




```
[root@localhost bin] # jconsole
```


![](./images/31.PNG)


![](./images/32.PNG)


Once the system is connected, it gives the complete overview of the
system such as the CPU, memory, thread, and classes. The following
screenshot shows the details. We can also do a deep analysis for the
following components of Java-based applications:

- Memory
- Thread
- Classes
- MBeans


The advantages of using this tool are:

- Online analysis of the application
- Customized report for the analysis
- Deadlock can be retrieved in the systems


### Different tabs for the JConsole and their features


We will now discuss the different components of monitoring for the
JConsole.


#### Memory overview


It\'s necessary for web administrators to analyze the memory status for
Tomcat 8 to avoid future issues with the server. The following
screenshot shows the real-time heap memory utilization for Tomcat 8.
This tab provides the following features:

- Graphical presentation of memory with their JVM footprints
- Customization of the Memory chart based on the requirement analysis
- Ability to perform the GC


![](./images/33.PNG)


#### Threads overview


This tab gives the complete picture of the server threads and the web
application hosted in Tomcat 8, for a particular instance. The following
screenshot shows the live status of the threads utilization, and the[
**Deadlock Detection** button is highlighted. In real-time,
this thread analysis tool is a very handy tool for the administrators.
Following are the features offered by the **Threads** tab:

- Graphical presentation of threads and their picture
- Individual thread analysis with their status
- Deadlock detection

![](./images/34.PNG)


#### VM Summary and Overview


These two tabs are very important for an administrator. In practice,
it\'s not possible for the administrator to view each and every
component of the application every time. What the administrator does is,
he/she checks for the overall performance of the system. If any
anomalies are found, they will drill down the component. Following are
the features of these tabs:

- Complete summary of the instances (**Heap Memory Usage, Threads,
    CPU Usage, Classes**)
- VM argument summary

![](./images/35.PNG)


The previous screenshot shows the real-time status of Tomcat 8. It
consists of four graphs displaying the real-time utilization of the
heap, threads, classes and CPU usage for the Tomcat 8 instance. On the
other hand, the following screenshot shows the complete summary of the
Tomcat instance:



![](./images/36.PNG)


#### MBeans


This tab gives you the complete picture of **Managed Beans**
(**MBeans**) deployed in the Tomcat instance. It includes
both Tomcat and application-level MBeans. The following screenshot shows
the attributes of **MBeans**. It\'s very useful if a
particular MBean is the source for an issue. Following are the advantages of the **MBeans** tab:


- All parameters used in one tab
- Easy-to-deploy, rollback, and invoke
- We can create a user at the database level using MBeans
- We can create notifications for events using MBeans
- Configuration for resources can be done dynamically

![](./images/port.PNG)



![](./images/37.PNG)


There are four types of MBeans. The following figure shows the different
types of MBeans. Let\'s discuss each MBean briefly:


- **Standard MBeans:** A standard MBean is a combination of
    an MBean interface and a class, where the interface defines the
    entire list of attributes and operations, while the class provides
    the functionalities for communication for a remote interface. It is
    one of the simplest MBeans.
- **Dynamic MBeans:** A dynamic MBean implements a
    separate interface (a specific method) and can be invoked at
    runtime.
- **Open MBeans:** It is a composition of Dynamic MBeans
    and the universal dataset used for manageability.
    
- **Model MBeans:** It is a composition of Dynamic MBeans
    with complete access to configurable parameters at runtime and
    self-described methods. This MBean requires classes.

![](./images/beans.PNG)

Let\'s take an example of the Connectors deployed in Tomcat 8, where we
can configure and perform operations on the Connectors remotely using
MBeans. By default, the HTTP and AJP Connectors are configured. In our
example, we have the HTTPS Connector also configured. The following
screenshot shows the three Connectors HTTP, AJP, and HTTPS:


![](./images/41.PNG)


If we observe the **Connector** folder, we can view the three
sublevels for each Connector. Following are the functions of each
section:

- **Attributes:** This section contains information about
    the different parameters loaded in the memory during the startup of
    the Tomcat instance. In short, we can say that information of the
    configured parameter is loaded at runtime.
- **Operations:** The functionality of this mode is to
    perform runtime operations for MBeans. Following are the different
    operations we can perform:

- Destroy
- Start
- Stop
- Init
- Resume
- Pause

![](./images/42.PNG)


The following screenshot shows the pause operation successfully invoked for the HTTP Connector for Tomcat 8:

![](./images/43.PNG)


**Note:** Open ` http://localhost:8080`. We then find the Tomcat welcome
page is not being displayed, run `Resume` function and check again.



Summary
-------------------------


In this lab, we have discussed the various processes of monitoring
in Tomcat 8 and their components using the Tomcat Manager and JConsole,
such as different ways of monitoring, how monitoring is done in Tomcat
7, JConsole, and how it is used. In the next lab, we will discuss
the high availability setup for Tomcat 8 using clustering, load
balancing, high availability concepts, architecture design, scalability,
and so on.
