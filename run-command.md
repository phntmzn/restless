`npx restless init` initializes **[Restless](chatgpt://generic-entity?number=0)** in your existing project.

Restless helps automatically generate API documentation, create an OpenAPI specification, install an SDK, and build an interactive developer portal.

### 1. Run the command

Open your project directory in Terminal:

```bash
cd your-project
npx restless init
```

### 2. What happens?

The interactive setup will:

1. Detect your backend framework.
2. Find or generate an OpenAPI specification.
3. Install the Restless SDK.
4. Configure your API.
5. Connect your project to a Restless account.
6. Set up an API developer portal.

### 3. Supported frameworks

| Language | Frameworks |
|---|---|
| Python | FastAPI, Flask, Django |
| JavaScript | Express, Hono, Koa |
| TypeScript | Next.js, NestJS, Fastify |
| Go | Gin, Echo, Chi |
| Ruby | Rails, Sinatra |

### 4. Important files

Restless creates:

```text
your-project/
├── .restless/
│   └── OpenAPI configuration
├── .env
│   └── RESTLESS_KEY
├── src/
└── package.json
```

Keep `RESTLESS_KEY` private. Don't commit `.env` to GitHub.

**Documentation:** [oai_citation:0‡restless.ai](https://www.restless.ai/getting-started?utm_source=chatgpt.com)

### What makes it interesting?

If you're building an API with Python, FastAPI, or React/TypeScript, Restless can help turn your backend into a documented, developer-friendly API platform.