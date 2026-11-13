# Teaching Materials for Discrete Methods in Modern AI

This repository contains the teaching materials for the "Discrete Methods in Modern AI" course given at the University of Tübingen (Winter Semester 2026/2027).

### Course Description 

In this course, we examine applications of discrete modeling techniques to problems in modern language modeling and generative AI. We will study how such techniques -- drawn from logic, automated reasoning, and classical probabilistic inference -- can support deeper semantic analysis of current systems, provide a means of incorporating structured knowledge and constraints into learning and inference, and offer theoretical tools for characterizing their capabilities and limitations. More specifically, we will introduce methods for [SAT solving](https://en.wikipedia.org/wiki/Boolean_satisfiability_problem) and related problems (e.g., [propositional model counting](https://www.sciencedirect.com/science/article/pii/S0004370207001889)), [tractable logical and probabilistic inference](https://arxiv.org/abs/2202.02942), and [probabilistic programming](https://en.wikipedia.org/wiki/Probabilistic_programming), focusing on their applications to [next-token modeling](https://arxiv.org/abs/2609.13520), [learning with logical constraints](https://arxiv.org/abs/1909.00126), [preference-based post-training](https://arxiv.org/abs/2412.17696), [prompting](https://starai.cs.ucla.edu/papers/RichardsonTPM26.pdf), and [test-time inference](https://aclanthology.org/2022.emnlp-main.115/).

**Materials and Evaluation** The lectures and accompanying materials given here will provide a self-contained presentation of the core course content, drawing on research papers from the field. Students will be expected to engage with assigned readings each week, which will provide additional depth and exposure to the original research. The course will have a **hands-on** component: programming exercises will be provided that allow students to implement the methods discussed in class and develop a concrete understanding of how they work. Course evaluation will largely be **project-based**: students will be asked to pursue research projects that dig deeper in the core course content.

**Requirements**: This course is intended for advanced bachelor/master students in [ISCL](https://uni-tuebingen.de/en/faculties/faculty-of-humanities/departments/modern-languages/department-of-linguistics/courses-of-study/courses-of-study-at-the-sfs/international-studies-in-computational-linguistics/ba-programme-iscl/), as well as students in both the [cognitive science](https://uni-tuebingen.de/en/study/finding-a-course/degree-programs-available/detail/course/cognitive-science-master/) and [machine learning](https://uni-tuebingen.de/fakultaeten/mathematisch-naturwissenschaftliche-fakultaet/fachbereiche/informatik/studium/studierende/lehre-studienorganisation/studiengaenge/machine-learning/) master programs. It requires knowledge of Python, basic machine learning (e.g., deep learning) and discrete mathematics (e.g., classical logic and discrete probability). Knowledge of language modeling is not strictly required, we will go through the basics together through concrete examples. We will also cover the more advanced discrete modeling techniques in a self-contained manner. 

Time and Location 
==========

Monday 12:00-14:00PM, Hörsaal 7 ([Alte Archäologie](https://maps.app.goo.gl/2b5BaPw8gPyS8sHi6)). $\color{red}{\text{Please note:}}$ The class will begin later in the semester on **November 2nd**. 

Lecturer
==========

[**Kyle Richardson**](https://www.krichardson.me/)

Slides and schedule 
==========

*Foundations*

[**lecture 1**](https://github.com/TuLLI-AI/DiscreteMethodsAI/blob/main/slides/lecture1.pdf): course overview, **discrete modeling foundations**, [**background** 🔒](https://drive.proton.me/urls/QKZSNH56Y8#Kce8tUoLYg0d) [[📓 **notebook**](https://github.com/TuLLI-AI/symprog/blob/main/notebooks/solver_tutorial.ipynb)]

[**lecture 2**](https://github.com/TuLLI-AI/DiscreteMethodsAI/blob/main/slides/lecture2.pdf): **language modeling basics**, [**transformers**](https://arxiv.org/abs/1706.03762), [**RASP**](https://arxiv.org/pdf/2106.06981). [[📓 **notebook**](https://github.com/TuLLI-AI/DiscreteMethodsAI/blob/main/notebooks/lecture2_code.ipynb)]

*Applications*

[**lecture 3**](https://github.com/TuLLI-AI/DiscreteMethodsAI/blob/main/slides/lecture3.pdf): declarative approaches to **model training and fine-tuning**, the [**semantic loss**](https://arxiv.org/pdf/1711.11157) and [**weighted model counting**](https://www.sciencedirect.com/science/article/pii/S0004370207001889),  [**other**](https://arxiv.org/abs/1909.00126) approaches. [[📓 **notebook**]([https://github.com/TuLLI-AI/symprog/blob/main/notebooks/semantic_loss.ipynb](https://github.com/TuLLI-AI/DiscreteMethodsAI/blob/main/notebooks/lecture3_code.ipynb))] [[📓 **SL notebook**](https://github.com/TuLLI-AI/symprog/blob/main/notebooks/semantic_loss.ipynb)]

**lecture 4**: declarative and probabilistic approaches to **next-token prediction** and pre-trained model evaluation [**modellog**](https://arxiv.org/abs/2609.13520), [**LLM sampling**](https://arxiv.org/abs/1904.09751)

**lecture 5**: high-level programming techniques for [**direct preference alignment**](https://arxiv.org/abs/2305.18290) and [**LLM alignment**](https://www.jair.org/index.php/jair/article/view/17541), [**formal characterizations**](https://arxiv.org/abs/2412.17696) of *known* loss functions. 

**lecture 6**: probabilistic programming for test-time inference [**Discrete Probabilistic Programming (PPL)**](https://arxiv.org/abs/1904.02079), [**Chain-of-thought prompting**](https://arxiv.org/abs/2201.11903) [**PPLs for CoT**](https://starai.cs.ucla.edu/papers/RichardsonTPM26.pdf) 

Symprog 
==========

In this course, we will use the [symprog](https://github.com/TuLLI-AI/symprog) library to help implement and better understand the concepts introduced in the class. Please see there for more details and installation instructions. 

Below is an example involving performing inferences over weighted Boolean formulas: 
```python
## pip install symprog
from symprog import Solver

solver = Solver()

FORMULAS = [
    "Implies(a, b)",
    "And(Or(a, b), Implies(a, c))"
]
solver.add(FORMULAS)
solver.add_weights({"a": 0.9, "b": 0.64, "c": 0.34})
print(solver.query())
```

Other Helpful Resources 
==========

Below are some pointers to code resources:
- **Discrete math**: [[intro logic]](https://github.com/TuLLI-AI/IntroLogic)
- **languages** [[scallop]](https://github.com/scallop-lang/scallop), [[problog]](https://github.com/ML-KULeuven/problog), [[pyDatalog]](https://github.com/pcarbonn/pyDatalog), [[lmql]](https://github.com/eth-sri/lmql),[[rasp]](https://github.com/tech-srl/RASP), [[NumPy Rasp]](https://github.com/apple/ml-np-rasp), [[deepproblog]](https://github.com/ML-KULeuven/deepproblog) 
- **automated reasoning tools/circuits** [[Z3 solver]](https://github.com/Z3Prover/z3), [[python-sat]](https://pysathq.github.io/), [[pysdd]](https://github.com/wannesm/PySDD), [[cirkit](https://github.com/april-tools/cirkit)] 
- **NLP and general ML** [[transformers]](https://github.com/huggingface/transformers), [[PyTorch]](https://pytorch.org/), [[pylon-lib]](https://github.com/pylon-lib/pylon), [[hf datasets]](https://huggingface.co/docs/datasets/index), [[hf hub]](https://huggingface.co/docs/hub/en/index)
- **other useful utilities** [[sympy]](https://www.sympy.org/en/index.html)

**Useful tutorials**: [**Transformers from scratch**](https://peterbloem.nl/blog/transformers) (*some examples/ideas used in lecture 2*), [**Lectures on Probabilistic Programming**](https://www.khoury.northeastern.edu/home/sholtzen/oplss24-ppl/), [**Tractable Probabilistic Models**](https://web.cs.ucla.edu/~guyvdb/slides/TPMTutorialUAI19.pdf)
