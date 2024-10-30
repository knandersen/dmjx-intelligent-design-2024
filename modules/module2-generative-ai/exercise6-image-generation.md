# Exercise 6: Image Generation

In this exercise, we will shift our focus towards image generation. Since you already have experience with basic image generation, this exercise will mainly focus on two things:

- Manipulating existing images
- Exploring Stability image APIs
- Using image manipulation as a material for your own projects

There are a few different providers, but I picked [Stability](https://stability.ai) for us to use since they provide many ways of manipulating images.

Stability offers many different models, but we will use [Stable Image Core](https://platform.stability.ai/docs/api-reference#tag/Generate/paths/~1v2beta~1stable-image~1generate~1core/post), which is optimized for speed and price.

The price for an image operation varies from 3-9 credits ($0.03-$0.09).

To get you started, I have created a Vue.js project that you can use as the base:

https://github.com/knandersen/stability-quickstart-vue

## Exercise 6.1: First image

Generate your first image by cloning the repository above, following the installation instructions and trying out the website

1. Create your Stability account: https://platform.stability.ai/account (using your Google account will give you 25 free credits)
2. Clone the github repository above and install packages
3. Start the development server and go to the Vite URL
4. Click the `generate`-button and wait a few seconds
5. If a generated image of a cat in a spacesuit appears, you have set the project up right and made your first successful Stability API call

_If an image does not appear, open your browser console and check for any errors._

## Exercise 6.2: Explore the API

In Exercise 6.1, you generated an image, but now it's time to learn more about the API. Go to Stability's Documentation under [API Reference](https://platform.stability.ai/docs/api-reference).

_NOTE: This isn't easy, so be patient with yourselves while reading through the documentation. If you get stuck, do me a favor: Instead of asking ChatGPT for the code, ask ChatGPT to help you study the documentation. Give ChatGPT a link to the documentation site or export the documentation to a PDF and upload it. This is a much better learning experience, and a good practice to get into._

![Screenshot of Stability Documentation: API Reference](/assets/ex6-stability-api-reference-menu.png)

Notice the menu on the left? In Exercise 6.1, you used `Stable Image Core` to `Generate` an image.

1. Use the navigation menu to find the documentation for `Stable Image Core`.
2. It might seem a bit intimidating, but spend some time reading the documentation. Read the description, `"How to use"` section. Notice the highlighted text like `POST`, `authorization` and `accept` header? Go back to the example code you worked with in the previous exercise and locate them.
3. Now go back to the documentation. It says that the body of an API request should include a `prompt`, but that it might also optionally include other parameters. Look further down the documentation page to find out more about these parameters.
4. Add one or more of the optional parameters to the example code and generate some more images.
5. Add UI controls to the component so that the parameters can be changed by the user in an easy way.

## Exercise 6.3: Try out more API endpoints

That website contains all the documentation on how we can talk to the API, and what kinds of requests we can make:

1. Generate (which you did in Exercise 6.1)
2. Upscale
3. Edit
4. Control

Each of these four categories has multiple services. You can see visual examples of them here: https://stability.ai/stable-assistant

Pick one that you think looks fun or interesting, and check out the documentation for it. What do you need to include in your API call and how can you modify the initial example code to achieve it?

There's already a `generateImage()` function. If you want to use the `Search and Recolor` feature, create a `searchAndRecolor()` function and use the same approach.

_TIP: Some of the endpoints require an image as input. Can you use the `ImageToImage.vue`-component for this? Sending the image to the Stability API can be a bit tricky, since it needs to be sent as a **binary string**. If you struggle to get the code to work, before reaching out for help, try to at least write the pseudo-code for how you think it should work_

## Exercise 6.4: Sketch

You may already have encountered this in the previous exercise, but some of the API services (eg Erase/Inpaint/Outpaint) require a `mask` as input. Reading about the mask, we have two options, either:

1. Send a separate image as a black/white mask (see screenshot below)
2. Use the alpha-channel of our existing image as the mask (ie erase pixels)

![Screenshot of how a mask can be used for editing purposes](/assets/ex6-masking.png)
_Screenshot from: https://huggingface.co/docs/diffusers/en/using-diffusers/inpaint_

As part of the starter project, there is a `Sketch`-component. Notice how you can draw on it with a brush to erase pixels.

1. Study the `Sketch.vue`-code. How does it work?
2. Can you change the way the brush works? Suggestions:
   - Change the brush to draw pixels instead of erasing? Could be used for the Sketch-to-image-service
   - Change the size/shape of the brush and provide UI controls for how to do this
3. Can you tie `Sketch.vue` and `ImageToImage.vue` together, so that you can sketch on the left, and it becomes an input image for an Image-to-image service without downloading the image first?
