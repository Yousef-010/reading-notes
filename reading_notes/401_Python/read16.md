# Reading 16 
> Serverless Functions
- Vercel Serverless Functions enable running code on-demand without needing to manage your own infrastructure
- provision servers, or upgade hardware.
- Functions (Lambda) enable developers to write functions in JavaScript and other languages to handle user authentication,
- form submissions, database queries, custom Slack commands
- These Functions are co-located with your code and part of your git workflow
- As traffic increases, they automatically scale up and down to meet your needs
- helping you to avoid downtime and paying for always-on compute.


> Deploying Serverless Functions
- To deploy Serverless Functions without any additional configuration,
- you can put files with extensions matching supported languages and exported functions in the /api directory at your project's root.
- Sometimes, you need to place extra code files, such as utils.js, inside the /api folder. 
- To avoid turning them into API endpoints, prefix such files with an underscore, _utils.js.
- Files with the underscore prefix are not turned into Serverless Functions.
- push to your connected Git repository using a Vercel for Git to receive a deployment automatically. 

>> Example Serverless Function with Next.js
```
// pages/api/index.ts
import { NextApiRequest, NextApiResponse } from 'next';
export default function handler(
  request: NextApiRequest,
  response: NextApiResponse,
) {
  response.status(200).json({
    body: request.body,
    query: request.query,
    cookies: request.cookies,
  });
}
```

>> Environment Variables
- You can use Environment Variables inside your Serverless Functions, both locally with vercel dev as well as deployed to Preview and Production environments.
- Example
```
CLIENT_ID="your-value"
CLIENT_SECRET"your-value"
```

```
import fetch from 'node-fetch';
export default async function handler(request, response) {
  const res = await fetch('https://...', {
    method: 'POST',
    body: JSON.stringify({
      client_id: process.env.CLIENT_ID,
      client_secret: process.env.CLIENT_SECRET,
    }),
    headers: { 'Content-Type': 'application/json' },
  });
  const data = await res.json();
  return response.status(200).json({ data });
}
```

>> Path Segments 
- Deploying Serverless Functions with Vercel gives you the ability to use path segments through file names instead of a complex routes file.
- Any supported languages can utilize path segments. 
- Creating a file in the /api directory and wrapping the filename in square brackets,
- such as [name].js will provide you with a file that takes a path segment and gives it to the function when requested with a value.
- **Note: When using path segments, the value passed is made available to the req.query object under the key used for the file name.**

> Execution Timeout 
- Serverless Functions on Vercel enforce a maximum execution timeout.
- This means that the function must respond to an incoming HTTP request before the timeout has been reached.
- If the Serverless Function does not respond to the HTTP request within the timeout,
- then a 504 error status code is returned with the error code FUNCTION_INVOCATION_TIMEOUT.


>>> Timeout conditions checklist
- The function isn't returning a response:
  - The function must return an HTTP response, even if that response is an error. If no response is returned, the function will time out.
- The function is taking too long to process a request: 
  - Check that any API, or database requests you make in your function
  - are responding within the "Serverless Function Execution Timeout (Seconds)" limit applicable to your plan.
- You have an infinite loop within your function: 
  - Check that your function is not making an infinite loop at any stage of execution.
- Upstream errors: Check that any external API or database that you are attempting to call doesn't have any errors.


> Error Logs
- Logs are treated as an "error" when Serverless Functions do not return a correct response by either crashing or timing out.
- The last 2,000 error logs are stored and persisted indefinitely.

>> Local Development
- Vercel provides an additional command with Vercel CLI to help you develop Serverless Functions locally by
- replicating the production environment on Vercel with your localhost.
- **Note: If you are using Next.js, you should continue to use the Next.js CLI instead.**

> Logging Serverless Functions 
- Each deployment at Vercel has a Functions section where you can see the calls to your Serverless Functions in real time.
- In order to log the functions properly, leave the Functions section open while your deployment is being accessed in the browser.
![image](https://vercel.com/docs-proxy/_next/image?url=%2Fdocs-proxy%2Fstatic%2Fdocs%2Fcommon%2Fdeployment-functions.png&w=750&q=75)


> Resources 
- Limits 
  - https://vercel.com/docs/concepts/limits/overview#serverless-function-size 
  - https://vercel.com/docs/concepts/limits/overview#serverless-function-memory
  - https://vercel.com/docs/concepts/limits/overview#serverless-function-concurrency
  - https://vercel.com/docs/concepts/limits/overview#serverless-function-payload-size-limit
  - https://vercel.com/docs/concepts/limits/overview#general-limits
- https://vercel.com/docs/concepts/functions/serverless-functions#limits
- https://newrelic.com/blog/best-practices/create-a-serverless-function-in-python
