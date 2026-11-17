# Udagram Image Filter Microservice

Course project for the Udacity **Cloud Developer Nanodegree** (2020): a small Node.js/Express service in TypeScript that downloads an image from a public URL, applies a filter, and returns the result. Deployed to AWS Elastic Beanstalk.

## What I built

- `GET /filteredimage?image_url=<URL>` in [`src/server.ts`](src/server.ts)
  - returns `400` when `image_url` is missing
  - filters the image with the provided helper (`filterImageFromURL`) and sends the file back
- Deployed with the Elastic Beanstalk CLI (`eb init`, `eb create`, `eb deploy`)
- A Postman collection to test the endpoint: [`cloud-cdnd-c2-final.postman_collection.json`](cloud-cdnd-c2-final.postman_collection.json)

![Elastic Beanstalk environment](deployment_screenshots/screenshot_beanstalk.png)

![Response from the deployed endpoint](deployment_screenshots/response_screenshot.png)

## Run locally

```bash
npm i
npm run dev   # http://localhost:8082/filteredimage?image_url=<public image URL>
```

## Notes

- The cleanup call (`deleteLocalFiles`) is placed after `return`, so temporary files are never removed. It should run after the response finishes (for example in `res.on('finish', ...)`).
- The starter code and helper functions come from Udacity's [cloud-developer](https://github.com/udacity/cloud-developer) repository.
