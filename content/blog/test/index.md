---
title: Thinking about LLM as a judge
---

Assessing the performance of a software system is essential for developers and application builders. Whether creating a simple web app or a complex social network, it's crucial to measure content quality, user experience, and long-term value of the features that you build.

Historically, evaluation methods have ranged from simple engagement metrics to human-based assessments and complex econometric models. However, the rise of Large Language Models (LLMs) has introduced a novel approach: LLM-as-a-judge.

LLM-as-a-judge takes advantage of LLMs varasitilty to provide easy evaluation. By defining specific evaluation criteria and providing data, LLMs can offer comprehensive assessments, including verdicts, explanations, and improvement suggestions. This unified approach simplifies the evaluation process, making it easier to identify strengths, weaknesses, and potential areas for optimization. This new approach while not a selver bullet, it could be a greate addition to software evaluation tools you can use of your projects.

### Example of LLM-as-a-judge
Let us take a simple example, imagine we are developing an app to help people learn about places they want to visit. Lets say a user lands on a page talking about specific city, like Berlin. We can start from exploring exisitng options like Wikipedia, bing and google search as shown in the table below. You can already observe, due to limited page realestate, UX provided by google and bing provide the user with more leads for further reading and allow interactivty to some degree. In such chase, you don't even need an A/B test to tell that wikipeida is not the right way to go!

<style>
.responsive-table {
  width: 100%;
}

.responsive-table td {
  display: block;
  text-align: center;
}

.responsive-table img {
  max-width: 100%;
  height: auto;
}
</style>

<table>
  <tr>
    <td><img src="wikipedia_berlin_page.png" class="responsive-table" width="100%" /></td>
    <td><img src="bing_search_berlin.png" class="responsive-table" width="100%" /></td>
    <td><img src="google_search_berlin.png" class="responsive-table" width="100%" /></td>
  </tr>
</table>

Now, that we say how it looks like, lets revert to LLM-as-a-judge and see how it goes. I will use the following promopt and call 


```text
You are an AI agent who judge UX, your task is to select the best UX for an app used for exploring places to visit. You will be provided with multiple screenshots and your task is to evaluate which one is the best UX. 

Pleas think step-by-step and provide exntinsive evaluation of the screenshots, focus on the ability of users to learn about places to visit and get the right information for thier forthcomming trip. 

Answr in a tabular formate.```



Input Data:

Screen shot 1:
image_1.png

Screen shot 2:
image_2.png

Screen shot 3:
image_3.png

Answer:
```

| Criteria | Screenshot 1 | Screenshot 2 | Screenshot 3 |
|---|---|---|---|
Clarity and conciseness | Information is clear and concise, but the overall presentation is basic. | Information is clear and concise, with a more engaging layout. | Information is clear and concise, similar to Screenshot 2. |
Relevance |	Provides a relevant overview of Berlin as a city, including population and notable landmarks. | Provides a relevant overview of Berlin, with a focus on visual appeal. | Provides a relevant overview of Berlin, similar to Screenshot 2. |
Navigation | N/A (single-page screenshot) | Basic navigation structure with a clear header and footer. | Basic navigation structure with a clear header and footer. |
Visual appeal |	Simple and functional, but lacks visual interest. |	Engaging design with a large hero image and weather information. |	Similar to Screenshot 2, with a focus on visual appeal. |
Overall evaluation | A good starting point, but lacks visual appeal and navigation. | Offers a more engaging experience with a focus on visual appeal and basic information. | Similar to Screenshot 2, but could benefit from more detailed information about specific places to visit. |

```text
Final Verdict: Screenshot 2 offers the best overall UX due to its engaging design and relevant information. However, all three screenshots could benefit from improved navigation and more detailed information about specific places to visit.
```

As you can see, the LLM judge provides good explanations and detailed evaluation based on the background knowladge it gain from the webscale training data. Now that we got the teaser, lets talk about some cool use-cases for using this evaluation methodology.


### LLM-as-a-judge patterns
#### Accelerate innovation (befoer you go to AB testing)
A/B testing is the defacto experimentation method every one use to evaluate if a feature A is better than feature B. It involves randomly dividing users into two groups and showing each group a different version. By analyzing the results, you can make data-driven decisions about which version is more effective. Usualy, people rely on p-values or baysian analysis to report the statistical significance of the gain of featuer A compared to featuer B. 

A/B testing, while a powerful tool for evaluating different versions of a feature, is not without its limitations. While p-values and Bayesian analysis offer statistical insights, they may not always provide a complete picture.

One challenge is the requirement for large sample sizes or significant differences between versions to achieve statistical significance. This can be particularly problematic when evaluating subtle changes or features with smaller impacts. Even when statistical significance is reached, the business impact may be minimal or even negative. For instance, a promotion or marketing campaign might lead to short-term losses but long-term gains from attracting new users.

Furthermore, A/B testing doesn't provide a clear explanation for why one version is better than another. While it can identify a winner, it doesn't reveal the underlying reasons for the difference in performance. This can make it difficult to learn from the results and improve future iterations.

Finally, the effectiveness of a feature can change over time. A version that performs well in an A/B test might have negative consequences in the long run. For example, a feature that initially increases user engagement could lead to product fatigue or decreased user satisfaction over time.

To illustrate these challenges, let's consider a hypothetical example:

Imagine a travel guide app that introduces a new filtration functionality to allow users to filter destinations based on their interests, such as "sightseeing" or "nature lovers." An A/B test could be conducted to compare the performance of the new filtration feature with the existing search functionality.

However, even if the new filtration feature proves to be statistically significant in terms of user engagement or conversions, several questions remain:

- Business impact: Is the increase in user engagement or conversions sufficient to justify the development and maintenance costs of the new feature?
- Long-term effects: Could the new filtration feature lead to product fatigue or decreased user satisfaction over time?
- Underlying reasons: What specific aspects of the new filtration feature are driving the improved performance?

LLM as judge can help accelarating innovation. Instead of relying solely on real-world user data, which can be time-consuming to collect and analyze, LLMs can be trained on extensive datasets of user interactions and feedback. These models can then provide swift evaluations of various feature variations, identifying promising candidates or potential pitfalls before they are deployed to live users. This offline evaluation empowers teams to prioritize experiments more effectively, minimize the risk of releasing suboptimal features, and ultimately expedite the pace of innovation. 

*LLM as judge of supporting experimentation*:

Iterate offline, verify using A/B test


Build gurdrails and large scale automated tests


Dynamic evaluation criteria 


Extract surrogate features







Main point: before going into AB test, create features with LLM-as-a-judge, then fit a model.


----------
#### LLMs self improve 

#### Combine with synthetic data generation




#### Skill evaluation (human out of teh loop)

#### Skill evaluation (human out of teh loop)




### Can we use LLM-as-a-judge for evaluting machine learing and LLM systems?

The idea of an LLM serving as a judge is controversial. At first glance, it seems counterintuitive: if an LLM could recognize its own shortcomings, wouldn't it strive to rectify them? However, a deeper dive into the nature of intelligence reveals a fundamental asymmetry that makes this proposition plausible.

The Asymmetry of Intelligence

Intelligence, both human and artificial, exhibits a significant asymmetry between generative and discriminative capabilities. This means that entities can often comprehend and evaluate complex information more effectively than they can produce it. A simple analogy is the appreciation of art versus its creation. While many people can appreciate the intricacies of a masterpiece like "The Lord of the Rings," far fewer possess the creative talent to produce such a work.

LLMs and the Discriminative-Generative Gap

LLMs exemplify this asymmetry. They are adept at understanding and evaluating text, identifying patterns, and making informed judgments. This discriminative ability allows them to distinguish between good and bad arguments, correct information from misinformation, and even detect biases. However, their generative capabilities, while impressive, are often limited. They may struggle to produce truly original or nuanced content, especially when faced with complex or unfamiliar tasks.

Real-World Examples of the Asymmetry

This asymmetry is evident in various aspects of human and machine intelligence:

- Algorithm Optimization: Algorithms can be designed to optimize solutions to specific problems, but verifying the correctness of those solutions often requires different skills and techniques.
- Scientific Research: Scientists can evaluate the validity of experimental results and theories, but generating groundbreaking discoveries often involves a combination of creativity, intuition, and serendipity.
- Human Relationships: We can understand and respond to the emotions of others, but expressing our own feelings in a meaningful and authentic way can be challenging.

The Implications for LLMs as Judges

The discriminative-generative asymmetry suggests that LLMs, while not perfect, can be effective tools for legal decision-making. Their ability to understand and evaluate arguments, identify biases, and apply relevant laws makes them well-suited to the role of a judge. However, it is crucial to recognize the limitations of LLMs and ensure that they are used in conjunction with human oversight to prevent unintended consequences and ensure fairness.




### How to evaluate LLM-as-a-judge

why does it work ? 

why it is useful?





Taxonomy of skills to evaluate


Evaluation methods: 



Putting human in the loop

Pulling humna from the loop 

