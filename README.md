## Personal Setup
- upload PDF to ByteScale, get its details and manually insert all fields into DB table "Document" or will throw error when opening dashboard
- make sure Supabase Instance is running
- check PDF's corresponding vectors are in Pinecone

## Tech Stack

- Next.js [App Router](https://nextjs.org/docs/app) for the framework
- Mixtral through [Together AI](https://dub.sh/together-ai) inference for the LLM
- M2 Bert 80M through [Together AI](https://dub.sh/together-ai) for embeddings
- [LangChain.js](https://js.langchain.com/docs/get_started/introduction/) for the RAG code
- [Pinecone](https://www.pinecone.io/) for the vector database
- [Bytescale](https://www.bytescale.com/) for the PDF storage
- [Vercel](https://vercel.com/) for hosting and for the postgres DB
- [Clerk](https://clerk.dev/) for user authentication
- [Tailwind CSS](https://tailwindcss.com/) for styling

## Deploy Your Own

You can deploy this template to Vercel or any other host. Note that you'll need to:

- Set up [Together.ai](https://dub.sh/together-ai/)
- Set up [Pinecone](https://www.pinecone.io/) with 768 dimensions
- Set up [Bytescale](https://www.bytescale.com/)
- Set up [Clerk](https://clerk.dev/)
- Set up [Vercel](https://vercel.com/)
- (Optional) Set up [LangSmith](https://smith.langchain.com/) for tracing.

See the .example.env for a list of all the required environment variables.

You will also need to prepare your database schema by running `npx prisma db push`.

## Common errors

- Check that you've created an `.env` file that contains your valid (and working) API keys, environment and index name.
- Check that you've set the vector dimensions to `768` and that `index` matched your specified field in the `.env variable`.
- Check that you've added a credit card on Together AI if you're hitting rate limiting issues due to the free tier

## Future tasks

These are some future tasks that I have planned. Contributions are welcome!

- [ ] Add a trash icon for folks to delete PDFs from the dashboard and implement delete functionality
- [ ] Try different embedding models like UAE-large-v1 to see if it improves accuracy
- [ ] Explore best practices for auto scrolling based on other chat apps like chatGPT
- [ ] Do some prompt engineering for Mixtral to make replies as good as possible
- [ ] Protect API routes by making sure users are signed in before executing chats
- [ ] Run an initial benchmark on how accurate chunking / retrieval are
- [ ] Research best practices for chunking and retrieval and play around with them – ideally run benchmarks
- [ ] Try out Langsmith for more observability into how the RAG app runs
- [ ] Add demo video to the homepage to demonstrate functionality more easily
- [ ] Upgrade to Next.js 14 and fix any issues with that
- [ ] Implement sources like perplexity to be clickable with more info
- [ ] Add analytics to track the number of chats & errors
- [ ] Make some changes to the default tailwind `prose` to decrease padding
- [ ] Add an initial message with sample questions or just add them as bubbles on the page
- [ ] Add an option to get answers as markdown or in regular paragraphs
- [ ] Implement something like SWR to automatically revalidate data
- [ ] Save chats for each user to get back to later in the postgres DB
- [ ] Bring up a message to direct folks to compress PDFs if they're beyond 10MB
- [ ] Use a self-designed custom uploader
- [ ] Use a session tracking tool to better understand how folks are using the site
- [ ] Add better error handling overall with appropriate toasts when actions fail
- [ ] Add support for images in PDFs with something like [Nougat](https://replicate.com/meta/nougat)
