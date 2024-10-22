# Exercise 5: GPT API

In the previous exercise, you learned how to work with ChatGPT and use prompting to perform various tasks. The underlying model that powers ChatGPT is the GPT model, that is continuously updated with new training data and features.

You can use OpenAI's APIs to generate text, images, and other things that can be achieved in ChatGPT, but inside your own applications. Now, beyond a tool, GPT becomes a material you can use.

## Exercise 5.1: Your first GPT API call

1. Use your OpenAI account to log into https://platform.openai.com
2. If you haven't already, create a new project, generate a new API key and store it safely
3. Create a new javascript project folder and initialize a new project (either using your favorite framework or `bun/npm/pnpm/yarn init`)
4. Create a javascript file
5. Follow https://platform.openai.com/docs/guides/text-generation and copy the provided examples to your javascript file and run it

If you have experience challenges completing this exercise, there is a Vue example project here: https://github.com/knandersen/openai-quickstart-vue

**IMPORTANT:**
Because it's bad practice and would allow anyone else to use it and spend your money, OpenAI doesn't tell you to put your API key in the script. To make the examples work, create a secret `.env` file in your project root and define the `OPENAI_API_KEY` variable, eg:

```env
OPENAI_API_KEY=<YOUR_API_KEY>
```

If this doesn't work or you want to be even more explicit about using the environment variable, supply a `apiKey` argument that points to your environment variable when you initialize the `OpenAI` client:

```javascript
const openai = new OpenAI({
  apiKey: process.env.OPENAI_API_KEY,
});
```

## Exercise 5.2: Try different Completion parameters

There are parameters you can adjust to change how text is generated: https://platform.openai.com/docs/api-reference/chat/create

While this might seem like a very technical exercise, try to input the same prompt but with different parameters and notice how the response changes. Feel free to try whatever you want, but at least:

- `seed` https://platform.openai.com/docs/api-reference/chat/create#chat-create-seed
- `temperature` or `top_p` https://platform.openai.com/docs/api-reference/chat/create#chat-create-temperature

Bonus points for trying:

- `frequency_penalty` https://platform.openai.com/docs/api-reference/chat/create#chat-create-frequency_penalty
- `logit_bias` https://platform.openai.com/docs/api-reference/chat/create#chat-create-logit_bias
- `n` https://platform.openai.com/docs/api-reference/chat/create#chat-create-n
- `presence_penalty` https://platform.openai.com/docs/api-reference/chat/create#chat-create-presence_penalty

## Exercise 5.3: Play with ways of using the API

There are many ways of using GPT as a material and the field is emerging. A few design patterns I have investigated through my work with GPT as a material for thinking and creating are listed below. Use one or more of these design patterns to create small, fun applications.

### Time

ChatGPT requires you to manually prompt all the time, ie it doesn't do anything unless you tell it to. But using the GPT API, you can ask GPT to perpetually generate new text or iterate on the same text.

#### Examples

[Matt Webb's Poem/1 AI clock](https://www.kickstarter.com/projects/genmon/poem-1-the-ai-poetry-clock) uses GPT to generate small poems that indicate the current time

[super ultra idea factory](https://superultra.dk/projects/generative-ai#ideafactory) uses asynchronicity as a concept to generate images outside of human working hours

### Space

At super ultra we have found it interesting to play with space. Try to think spatially when generating text, eg does text get smaller/bigger? with time, or maybe with interaction? where on the screen might something live? why?

#### Examples

- [super ultra 3d autocomplete](https://superultra.dk/projects/generative-ai#autocomplete) uses space and plurality to place multiple simultaneously generated text strings

### Plurality

It's cheap and fast to generate multiple results at once with GPT. When asking GPT to generate something, try to ask to generate multiple of something.

#### Examples

- [super ultra idea factory](https://superultra.dk/projects/generative-ai#ideafactory) uses asynchronicity as a concept to generate images outside of human working hours
- [super ultra 3d autocomplete](https://superultra.dk/projects/generative-ai#autocomplete) uses space and plurality to place multiple simultaneously generated text strings

### Personality

Using the GPT system prompt, you can steer the generated content.

#### Examples

- [super ultra SlackGPT](https://superultra.dk/projects/generative-ai#slackgpt) uses personas to define team roles

- [super ultra Adventure Writer](https://superultra.dk/projects/generative-ai#adventurewriter) has a system prompt tailored to generating adventure style text

### Recursion

Can the text you generate using ChatGPT itself be part of your next prompt? Potentially creating a never ending stream of text. What kind of results does this yield?

### Text as a graphical element

Text itself can be a graphical element. Can you use GPT to return text in a way that makes it graphical? eg ASCII art, grids, etc.
