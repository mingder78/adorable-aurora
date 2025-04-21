# redis cloud

* test

```
ming-ders-MacBook.local💩➜  adorable-aurora git:(main) ✗ bun run index.ts
Connected to Redis!
Set key "myKey"
Value of myKey: Hello, Redis!
Disconnected from Redis
```
* code

```
ming-ders-MacBook.local💩➜  adorable-aurora git:(main) cat index.ts
// Import the Redis client
import { createClient } from 'redis';

// Define Redis connection details from Redis Labs
const redisConfig = {
  url: `redis://${import.meta.env.REDIS_USERNAME}:${import.meta.env.REDIS_PASSWORD}@${import.meta.env.REDIS_HOST}:${import.meta.env.REDIS_PORT}`,
};

// Function to connect to Redis and perform basic operations
async function connectToRedis() {
  try {
    // Create a Redis client
    const client = createClient(redisConfig);

    // Handle connection errors
    client.on('error', (err) => console.error('Redis Client Error:', err));

    // Connect to Redis
    await client.connect();
    console.log('Connected to Redis!');

    // Example: Set a key-value pair
    await client.set('myKey', 'Hello, Redis!');
    console.log('Set key "myKey"');

    // Example: Get the value of the key
    const value = await client.get('myKey');
    console.log('Value of myKey:', value);

    // Disconnect from Redis
    await client.quit();
    console.log('Disconnected from Redis');
  } catch (err) {
    console.error('Error:', err);
  }
}

// Run the function
connectToRedis();
```
* .env example

```
REDIS_USERNAME=your_username
REDIS_PASSWORD=your_password
REDIS_HOST=your_host
REDIS_PORT=your_port
```

* cloud redis
https://app.redislabs.com

## Astro with Tailwind

```sh
bun create astro@latest -- --template with-tailwindcss
```

[![Open in StackBlitz](https://developer.stackblitz.com/img/open_in_stackblitz.svg)](https://stackblitz.com/github/withastro/astro/tree/latest/examples/with-tailwindcss)
[![Open with CodeSandbox](https://assets.codesandbox.io/github/button-edit-lime.svg)](https://codesandbox.io/p/sandbox/github/withastro/astro/tree/latest/examples/with-tailwindcss)
[![Open in GitHub Codespaces](https://github.com/codespaces/badge.svg)](https://codespaces.new/withastro/astro?devcontainer_path=.devcontainer/with-tailwindcss/devcontainer.json)

Astro comes with [Tailwind](https://tailwindcss.com) support out of the box. This example showcases how to style your Astro project with Tailwind.

For complete setup instructions, please see our [Tailwind Integration Guide](https://docs.astro.build/en/guides/integrations-guide/tailwind).
