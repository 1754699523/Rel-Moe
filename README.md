# EpLSA
### Installing
 ```
transformers==3.3.1
torch==1.7.0
nltk==3.4.5
networkx==2.1
spacy==2.2.1
psutil==5.9.0

```
 
Training
The optimal parameters are provided in the script
Training anlg dataset
```
bash  scripts/train_anlg.sh
```
Training eg dataset
```
bash  scripts/train_eg.sh
```
Training seg dataset
```
bash  scripts/train_seg.sh
```
We will provide our trained checkpoints.

Inference

```
bash  scripts/predict.sh
```
The best hyperparameters setting of EpLSA on three tasks.
| Task      | $\alpha$ | $\beta$ | $\lambda$ |
|-----------|----------|---------|-----------|
| $\alpha$NLG | 1      | 0.5     | 2         |
| EG        | 0.05   | 0.05    | 2         |
| SEG       | 0.4    | 0.4     | 2         |


**Case Study**


We provide some test cases on three dataset.
In the example of abductive commonsense reasoning,  we aim to generate explanatory hypotheses when two observations are given: $O_{1}$ is the cause and $O_{2}$ is the effect. In this case, the semantic context of the $O_{1}$ and $O_{2}$ is that a cabinet is handmade. From the examples in Table \ref{tab_demo_anlgcase}, we can see EpLSA generates assumptions that include not only making it by hand yourself but also hiring professionals to do it, which is consistent with the contextual semantics and is highly diverse. The other methods appear to be heavily repetitive and frequently involve purchases.

In the explanation generation task, our purpose is to make explanations in the case of giving counterfactual statements. According to the generated examples in Table \ref{tab_demo_case_eg}, the interpretation generated by EpLSA ensures reasonableness compared to other methods and correctly explains the willingness of not being able to make a campfire with rocks while avoiding the generation of duplicate results.

The story ending generation task is to generate a reasonable ending given a four-sentence story context. Examples of the generation of several methods are shown in Table \ref{tab_demo_case_story}.  The results show that the EpLSA-generated story ending provides a remarkable summary of the narrative from a different perspective, encompassing the characters' emotions and driving experiences. The other models have different wrong summaries, such as "to the local zoo" of the MoE model.
| **Abductive Commonsense Reasoning**                          |
| ------------------------------------------------------------ |
| O1: I wanted some cabinets to put in my bedroom.<br/>O2: After two months of work I had crafted some beautiful cabinets ! |
| **MoE: (Shen et al., 2019)**                                 |
| (1) I went to the store to look for cabinets.<br/>(2) I went to the store to look for some.<br/>(3) I found some beautiful maple cabinets online and purchased them. |
| **Nucleus sampling: (Holtzman et al., 2020)**                |
| (1) I went to the store and bought cabinets.<br/>(2) I went to the store and bought some materials.<br/>(3) I went to the store and bought some materials. |
| **MoKGE: (Yu et al., 2022)**                                 |
| (1) I looked online for some cabinets. I buy some.<br/>(2) So I went to the store and purchased some new and beautiful cabinets.<br/>(3) I decided to put together some beautiful cabinets for my bedroom. |
| **EpLSA (Ours)**                                             |
| (1) I decided to hire a professional to make them.<br/>(2) I found some that I liked and decided to make them.<br/>(3) I spent a lot of time on to the store to look at different cabinets |





| Story Ending Generation                                      |
| ------------------------------------------------------------ |
| Statement:<br/>Juan was driving at night when he saw a shooting star.<br/>He stopped his car to look at the sky.<br/>Many more came and went before his eyes.<br/>He had been so depressed, the sight elated him. |
| **MoE: (Shen et al., 2019)**                                 |
| (1) Juan decided to take a trip to see more shooting stars in the future.<br/>(2) Juan decided to take a trip to the local zoo.<br/>(3) He decided to take a trip to see more shooting stars in the future. |
| **Nucleus sampling: (Holtzman et al., 2020)**                |
| (1) Juan decided to take a trip to the movies in the future.<br/>(2) Juan decided he would become a shooting star painter.<br/>(3) He decided to take a trip to the movies one day . |
| **MoKGE: (Yu et al., 2022)**                                 |
| (1) Juan decided to go home and take a long look at the stars.<br/>(2) Then he realized it was just another day and went home.<br/>(3) He took a deep breath and went back to reality. |
| **EpLSA (Ours)**                                             |
| (1) Juan drove off into the night sky happy and content.<br/>(2) He drove away feeling proud of himself for seeing such a sight.<br/>(3) Juan was glad he had decided to watch shooting stars. |


| Explanation Generation                                       |
| ------------------------------------------------------------ |
| Statement: Marry lit up rocks to make a campfire.            |
| **MoE: (Shen et al., 2019)**                                 |
| (1) Rocks are too heavy to make a campfire.<br/>(2) Rocks are not flammable and can’t be lit.<br/>(3) Rocks are not flammable and cannot be lit. |
| **Nucleus sampling: (Holtzman et al., 2020)**                |
| (1) Rocks are too hard to make a campfire.<br/>(2) Rocks are too hard to make a campfire.<br/>(3) Rocks are too hard to make a campfire. |
| **MoKGE: (Yu et al., 2022)**                                 |
| (1) Rocks are not flammable and can’t be lit.<br/>(2) You don’t make campfires with fire, you make fire with fire.<br/>(3) fire is used to make fire not to make campfire. |
| **EpLSA (Ours)**                                             |
| (1) Rocks don’t catch fire, so they can’t be used to make fire.<br/>(2) fire can not be lit up rocks, not burnt them.<br/>(3) Rocks don’t catch fire and would not make a campfire. |
