# Cymbal-Tagline-Generator-Template.
 
![Vertex AI](https://img.shields.io/badge/Google%20Cloud-Vertex%20AI-blue.svg)
![License](https://img.shields.io/badge/license-MIT-green.svg)
![Status](https://img.shields.io/badge/status-Completed-brightgreen.svg)

```markdown
# Prompt Design in Vertex AI: Challenge Lab

 

## Overview
In this challenge lab, you will apply the skills learned from the Prompt Design in Vertex AI and Gemini course to complete a series of tasks independently. The lab is designed to test your ability to create effective prompts and use them in real-world scenarios involving generative AI within Google Cloud's Vertex AI platform. Successfully completing all tasks within the given time period will result in a 100% score, evaluated by an automated scoring system.

## Topics Tested
- Crafting effective prompts and utilizing parameters to guide generative AI output in Vertex AI Studio.
- Applying Gemini models to create product descriptions and taglines for marketing campaigns.
- Running and modifying Python code exported from Vertex AI Studio to implement generative AI solutions.
- Using Jupyter Notebooks to test and refine generative AI code.

## Challenge Scenario
You're a member of an educational content startup specializing in engaging learners with the natural world. You've formed a partnership with Cymbal Direct, an online retailer launching a new line of outdoor gear and apparel designed to encourage young people to explore and connect with nature.

Cymbal Direct wants to create a marketing campaign for its new product line that leverages the power of generative AI. Your task is to help them develop a set of tools within Google Cloud's Vertex AI platform that will streamline the generation of the following:
- **Evocative Product Descriptions**: using image analysis to inspire short, descriptive text that captures the essence of their products and the feeling of being in nature.
- **Catchy Taglines**: focused on highlighting product features, the target audience, and the desired emotional response.

## Tasks

### Task 1: Build a Gemini Image Analysis Tool
In this section, you will create a template for analyzing images of Cymbal Direct products using the Gemini model in Vertex AI Studio. The goal is to generate descriptive text options inspired by the image, from simple details to more evocative, mood-setting phrases.

#### Steps:
1. **Download and Analyze Image**:
   - Download the provided product image from Cymbal Direct.
   - Use Vertex AI Studio's Multimodal interface and any of the gemini-1.0-pro-vision models to analyze the product image and generate multiple descriptive text options inspired by the image.
   - Experiment with different prompts to generate:
     - Short, descriptive text inspired by the image.
     - Catchy phrases suitable for advertisements.
     - A poetic description for a nature-focused campaign.

2. **Evaluate and Iterate**:
   - Adjust your prompt and parameters as needed to refine the results.

3. **Save the Prompt**:
   - Name your prompt "Cymbal Product Analysis".
   - Save the prompt in the us-central1 region.

   **Example Code**:
   ```python
   import base64
   import vertexai
   from vertexai.generative_models import GenerativeModel

   def generate_image_analysis():
       vertexai.init(project="your-project-id", location="us-central1")
       model = GenerativeModel("gemini-1.0-pro-vision")
       response = model.generate_content(
           ["""Describe this image with a focus on colors, textures, and the feeling it evokes."""],
           generation_config={"max_output_tokens": 50, "temperature": 0.7},
       )
       print(response)

   generate_image_analysis()
   ```

   **Output Image**:
   ![Image Analysis Output](path/to/your/image_analysis_output.png)

### Task 2: Build a Gemini Tagline Generator
In this task, you will create a structured prompt for generating diverse tagline possibilities using the Gemini language model in Vertex AI Studio. The goal is to develop a prompt that allows for customization of the tagline style, based on product attributes, target audience, and emotional resonance.

#### Steps:
1. **Create a Customizable Tagline Generator**:
   - Use the Gemini language model to design a structured prompt for generating taglines based on product attributes, target audience, and emotional resonance.
   - In Vertex AI Studio's Language interface, use any of the gemini-1.0-pro models to create a customizable tagline generator.

2. **Design a Structured Prompt**:
   - Include parameters to customize taglines based on:
     - Product attributes (e.g., durable, lightweight)
     - Target audience (e.g., young adventurers, families)
     - Emotional resonance (e.g., empowered, connected)
   - Example Context:
     ```
     Cymbal Direct is partnering with an outdoor gear retailer. They're launching a new line of products designed to encourage young people to explore the outdoors. Help them create catchy taglines for this product line.
     ```

3. **Include Examples**:
   - Example input and output:
     ```
     Input: Write a tagline for a durable backpack designed for hikers that makes them feel prepared. Consider styles like minimalist.
     Output: Built for the Journey: Your Adventure Essentials.
     ```

4. **Test and Refine**:
   - Experiment with different parameter combinations to see the variety of taglines produced.
   - Fine-tune the wording of your prompt, add more parameter options, or adjust the style choices to achieve your desired outcome.

5. **Save the Prompt**:
   - Name your prompt "Cymbal Tagline Generator Template".
   - Save the prompt in the us-central1 region.

   **Example Code**:
   ```python
   from vertexai.generative_models import GenerativeModel

   model = GenerativeModel("gemini-1.0-pro")

   prompt = """
   Cymbal Direct is partnering with an outdoor gear retailer. They're launching a new line of products designed to encourage young people to explore the outdoors. Help them create catchy taglines for this product line.

   input: Write a tagline for a [Product Attributes: durable, lightweight] backpack designed for [Target Audience: young adventurers] that makes them feel [Emotional Resonance: empowered]. Consider styles like minimalist.
   output: Built for the Journey: Your Adventure Essentials.
   
   input: Write a tagline for a [Product Attributes: rugged, compact] camping stove designed for [Target Audience: solo hikers] that makes them feel [Emotional Resonance: confident]. Consider styles like minimalist.
   output: Compact Power: Rugged Stove for Solo Confidence
   
   input: Write a tagline for a [Product Attributes: high-performance, waterproof] jacket designed for [Target Audience: professional climbers] that makes them feel [Emotional Resonance: safe]. Consider styles like minimalist.
   output: Peak Protection: High-Performance Waterproof Jacket
   
   input: Write a tagline for a [Product Attributes: versatile, easy-to-use] tent designed for [Target Audience: families] that makes them feel [Emotional Resonance: connected]. Consider styles like minimalist.
   output:
   """

   responses = model.generate_content(
       prompt,
       generation_config={"temperature": 0.5, "max_output_tokens": 2048, "top_p": 1.0, "top_k": 40},
       stream=True
   )

   for response in responses:
       print(response.text)
   ```

   **Output Image**:
   ![Tagline Generator Output](path/to/your/tagline_generator_output.png)

### Task 3: Experiment with Image Analysis Code
In this task, you will explore the Python code for the image analysis prompt you created. You will then modify the prompt to be more specific and test the new prompt in a notebook.

#### Steps:
1. **Explore the Image Analysis Code**:
   - Open a JupyterLab notebook in the Google Cloud Console.
   - Create a new notebook file named `image-analysis.ipynb`.

2. **Install the Vertex AI SDK**:
   - Open a terminal window and run the following commands:
     ```sh
     pip install --upgrade google-cloud-aiplatform
     gcloud auth application-default login
     ```

3. **Use the Following Code**:
   ```python
   import base64
   import vertexai
   from vertexai.generative_models import GenerativeModel

   def generate():
       vertexai.init(project="your-project-id", location="us-central1")
       model = GenerativeModel("gemini-1.0-pro-vision")
       responses = model.generate_content(
           ["""Describe this image with a focus on colors, textures, and the feeling it evokes."""],
           generation_config={"max_output_tokens": 50, "temperature": 0.7}
       )
       print(responses)

   generate()
   ```

4. **Modify the Prompt**:
   - Change the wording of the prompt to be more specific and shorter than 10 words.
   - Modify the prompt code to encourage the model to produce the most creative, unusual, and unexpected descriptions.

5. **Save and Test**:
   - Save the changes to your code and rerun the notebook to verify the output.

   **Output Image**:
   ![Image Analysis Code Output](path/to/your/image_analysis_code_output.png)

### Task 4: Experiment with Tagline Generation Code
In this task, you will explore the Python code for the tagline prompt you created. You will then modify the prompt to include a specific keyword and test the new prompt in a notebook.

#### Steps:
1. **Create a New Notebook**:
   - Create a new notebook file named `tagline-generator.ipynb`.

2. **Add the Following Code**:
   ```python
   from vertexai.generative_models import GenerativeModel

   model = Gener

ativeModel("gemini-1.0-pro")

   prompt = """
   Cymbal Direct is partnering with an outdoor gear retailer. They're launching a new line of products designed to encourage young people to explore the outdoors. Help them create catchy taglines for this product line.

   input: Write a tagline for a durable backpack designed for hikers that makes them feel prepared. Consider styles like minimalist.
   output: Built for the Journey: Your Adventure Essentials.

   input: Write a tagline for a rugged, compact camping stove designed for solo hikers that makes them feel confident. Consider styles like minimalist.
   output: Compact Power: Rugged Stove for Solo Confidence

   input: Write a tagline for a high-performance, waterproof jacket designed for professional climbers that makes them feel safe. Consider styles like minimalist.
   output: Peak Protection: High-Performance Waterproof Jacket

   input: Write a tagline for a versatile, easy-to-use tent designed for families that makes them feel connected. Include the keyword nature.
   output:
   """

   responses = model.generate_content(
       prompt,
       generation_config={"temperature": 0.5, "max_output_tokens": 2048, "top_p": 1.0, "top_k": 40},
       stream=True
   )

   for response in responses:
       print(response.text)
   ```

3. **Run the Code Cell**:
   - Verify that the code executes successfully and produces the expected output.
   - Ensure the new tagline includes the keyword "nature".

   **Output Image**:
   ![Tagline Generation Code Output](path/to/your/tagline_generation_code_output.png)

## Conclusion
By completing these tasks, you have successfully utilized Vertex AI's generative models to create compelling marketing content for Cymbal Direct. These tools will help Cymbal Direct launch their new product line and encourage young people to explore the outdoors.

## License
This project is licensed under the MIT License.

 

 
