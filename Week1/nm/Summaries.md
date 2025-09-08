
All 6 summaries and references&citation 
1.**Bayesian Hierarchical Model**

What is the goal of the paper? The authors aimed to develop a bayesian
hierarchical model for multivariate longitudinal data to predict the
health status, trajectory, and likely intervention effects for each
member of a clinical population in the PCORI mission, and to address
questions about health care from patients and clinicians.

Why is it important? Medical data includes DNA sequences, functional
images of the brain, patient-reported outcomes and the electronic health
record capturing patient’s sequence of health measurements, diagnoses,
and treatments. Full use of the electronic health record (EHR) of
patients could improve diagnostic accuracy and prediction of treatment
effects, since the standard approaches for analyzing clinical data are
not adequate for this purpose. The bayesian hierarchical model combines
diverse sources of prior knowledge and patient data with evidence, to
predict the patient’s health status, trajectory, and/or likely benefits
of interventions. Visualizations of characteristics of posterior
distributions can be immediately understood by clinicians and patients
as relevant to their decision.

How is it solved? – methods They applied Bayesian hierarchical
regression for multivariate longitudinal patient data using open-source
R-packages was developed 2 levels—time within person and persons within
a population The model comprised: the effects of exogenous (eg, age,
clinical history) and endogenous (eg, current treatment) variables on
the individual’s health status; multivariate health measurements for
health status; the effects of health measurements at one time on
subsequent interventions. The model produces an estimate of the
posterior distribution of the trend in health status for each value of
the predictor variables and produces an estimate of the marginal
distribution of the regression coefficients; each coefficient measures
how the outcome, health status, is associated with its predictor
variable (R, X). In a larger sample, the likelihood dominates the prior
distribution for key parameters such as regression coefficients. The
bayesian hierarchical model is adaptable because (1) it is a
likelihood-based approach.(2) use of priors (prior laboratory and
clinical trials data) provide a reasonable range for the assay
sensitivities that, once imposed through the prior assumptions, make the
model identifiable (3) Markov chain Monte Carlo (MCMC) estimate the
posterior distributions to avoid missing data and complex outcome
measurements.

Results/limitations, if any. Three case studies on pneumonia etiology in
children, prostate cancer, and major mental disorders, were chosen to
provide different challenges to the model development. In Prostate
Cancer Case Study to correctly identify low-risk patient population,
they developed and applied hierarchical model to possibly reduce the
risk overtreatment, complications and adverse effects from treatment, as
well as financial burden, for patients (Disease reclassification).
Prostate cancer software was then implemented within the JHM HER.
Limitation: the models were entirely parametric and recommend extensions
to nonparametric or more flexible parametric models. To have improved
approach for neuroimage or genomic data. @Zeger2020

2.  Bayesian Inference

What is the goal of the paper? The authors aim to apply computational
tool implementing Bayesian inference to calculate the posterior
probability of disease diagnosis to develop three modules designed to
define and compare parametric (with a fixed set of parameters) and
nonparametric distributions (which do not make a priori assumptions
about the distribution’s mathematical form) and analyses National Health
and Nutrition Examination Survey datasets from two separate diagnostic
tests on both diseased and nondiseased populations.

Why is it important? Medical diagnosis is crucial for treatment and
management decisions and uses conventional methods for diagnosis using
clinical criteria and fixed numerical thresholds limits capturing other
information about the intricate relations between diagnostic tests and
the varying prevalence of diseases. The probability distributions
associated with quantitative diagnostic test outcomes often demonstrate
some overlap between the diseased and nondiseased groups. Dichotomous
method fail to capture the complexity and heterogeneity of disease
presentations across diverse populations. The applicability of the
normal distribution in conventional method is critiqued, especially when
dealing with clinical measurands that exhibit skewness, bimodality, or
multimodality

How is it solved? – methods To authors explored and developed
specialized computational tool employing Bayesian inference (Bayesian
diagnostic approach) is to calculate the posterior probability of
disease diagnosis in theWolfram Language. Bayesian paradigm, calculates
and integrate prior probabilities of disease with distributions of
diagnostic measurands in both diseased and nondiseased populations, the
approach enables the evaluation of the information conveyed via
diagnostic measurements and the combination of data from multiple
diagnostic tests, to improve diagnostic accuracy and precision while
introducing flexibility, adaptability, and versatility into the
diagnostic proWhy is this important? Medical diagnosis is essential for
making treatment and management decisions. Conventional diagnostic
methods rely on clinical criteria and fixed numerical thresholds, which
limit the ability to capture other information about complex
relationships between diagnostic tests and the varying prevalence of
diseases. The probability distributions associated with quantitative
diagnostic test results often show overlap between the diseased and
nondiseased groups. Binary methods fail to reflect the complexity and
heterogeneity of disease presentations across diverse populations. The
use of normal distribution in traditional approaches is criticized,
especially when clinical measurements display skewness, bimodality, or
multimodality. How is this addressed? To tackle this, researchers have
developed specialized computational tools employing Bayesian
inference—also known as the Bayesian diagnostic approach—to calculate
the posterior probability of a disease diagnosis using the Wolfram
Language. The Bayesian paradigm combines prior disease probabilities
with the distributions of diagnostic measurements in both diseased and
nondiseased groups. This approach allows for the evaluation of the
information conveyed by diagnostic tests and the integration of data
from multiple tests, improving diagnostic accuracy and adaptability.
Establishing foundational data is crucial for providing the necessary
context to compare new measurements, and the lack of such normative data
can undermine the reliability and validity of Bayesian methods. Results
and limitations: Nonparametric Bayesian models tend to fit data
distributions better, especially given limited existing literature, and
are more robust in capturing complex data patterns. These models produce
multimodal probability patterns for disease, unlike the bimodal,
double-sigmoidal curves seen with parametric models. Limitations include
a reliance on parametric models with a need to extend to nonparametric
or more flexible parametric models, especially for neuroimaging or
genomic data. Limited scholarly publications lead to over-dependence on
prior probabilities. Insufficient data increases uncertainty, resulting
in broader confidence intervals for posterior probabilities. Systemic
bias from unrepresentative datasets can compromise the accuracy of
Bayesian calculations. Due to incomplete data, it is advisable to
combine Bayesian methods with other statistical and computational
techniques to enhance diagnostic capabilities. The foundational data is
crucial in establishing the essential context against which new
diagnostic measurements can be compared and the absence of such
normative data could potentially compromise the reliability and validity
of Bayesian diagnostic methods.

Results/limitations, if any. Nonparametric Bayesian models produce a
better fit to data distributions, considering limited existing
literature and emphasizes the robustness in capturing complex data
distributions. The nonparametric Bayesian probabilities for disease
exhibited multimodal patterns, in contrast to the bimodal, double
sigmoidal curves generated by parametric models.

Limitations: • The models were entirely parametric and recommend
extensions to nonparametric or more flexible parametric models and aim
to improv approach for neuroimage or genomic data. • Due to limited
availability of scholarly publications is an issue with over-dependence
on Prior Probabilities improve • Elevated Uncertainty due to
insufficient data contributes to broader confidence intervals in the
computed posterior probabilities • Systemic bias due to unrepresentative
datasets compromise the fidelity of Bayesian calculations. • Given the
lack of comprehensive data, it is pertinent to combine Bayesian methods
with other statistical and computational techniques for better
diagnostic modalities. @Chatzimichail2023

3.  Bayesian inference What is the goal of the paper? The study
    describes the stages of Bayesian analysis, specifying the prior and
    data models, deriving inference, model checking and refinement by
    discussing the importance of prior and posterior predictive
    checking, selecting a proper sampling technique from a posterior
    distribution, variational inference and variable selection and its
    application across various research fields. The study proposes
    strategies for reproducibility and reporting standards, outlining an
    updated WAMBS (when to Worry and how to Avoid the Misuse of Bayesian
    Statistics) checklist and also outline the impact of Bayesian
    analysis on artificial intelligence in the future.

Why is it important? Bayesian statistics is suitable for quantitative
researchers working across a broad range of science-related areas that
have at least some knowledge of regression modelling. We How is it
solved? – methods The study classified the priors into three categories
based on the degree of (un)certainty (hyperparameters) surrounding the
population parameter value: informative, weakly informative and diffuse.
The prior has its distribution as N( μ0 , σ\^ 20) where a larger
variance represents a greater amount of uncertainty surrounding. Prior
elicitation (experts, generic expert, data -based, sample data using
methods such as maximum likelihood or sample statistics, etc)
constructed prior distribution. Prior sensitivity analysis of the
likelihood, to examine different forms of the model assess how the
priors and the likelihood align and help understand the impact of the
prior settings on posterior estimates, reflecting the variation not
captured by the prior or likelihood alone. Prior estimation allow for
data-informed shrinkage, enact regularization or influence algorithms
towards a likely high-density region and improve estimation efficiency.
Knowing the exact probabilistic specification of the priors for a
complex model with smaller sample sizes is important as small sample
convey less information, compared to priors. To quantify the strength of
observed data lends to possible value(s) for the unknown parameter(s).

In Bayesian inference, unknown parameters (random variables) have values
that are varied while the (observed) data have values that are fixed,
and the likelihood is a function of θ for the fixed data y. Therefore,
the likelihood function summarizes a statistical model that
stochastically generates all of the data, a range of possible values for
θ and the observed data y.With having the prior, the likelihood, and the
data, we obtain posterior distribution we model to the data to estimate
the unknown parameters of the model. The model captures the primary
factors that we wish to improve our understanding of. Monte Carlo
integration technique provide integrals using computer simulations of
sampled values from a given distribution.The author mentioned packages
BRMS and Blavaan in R for simplifying the use of the probabilistic
programming language Stan.

Variable selection after checking correlations among the variables can
be easily incorporated into the analysis (ex- gene-to-gene interaction)
to aid the identification of predictive genes in biomedical research.
(genome-wide association studies). Spatial and temporal variability can
be factored into Bayesian general linear models. A posterior
distribution for a particular model can be used to simulate new data
conditional on this distribution to assess and provides valid
predictions to be used for extrapolating to future events.

Results/limitations, if any. Bayesian approaches resulted in analyzing
large-scale cancer genomic data sets to identify novel molecular changes
that lead to cancer initiation and progression. It helps to identify the
interactions between mutated genes and capture mutational signatures
that highlight key genetic interactions with the potential to allow for
genomic-based patient stratification in both clinical trials and the
personalized use of therapeutics and assists in answering questions
about evolutionary processes in cancer.

Limitations: In temporal models, posterior inference challenges are
inherent to spatial and/or temporal dependencies, such as
autocorrelation of parameters over time. @VandeSchoot2021

4.  Bayesian Normal linear regression

    What is the goal of the paper? The author provides guidance on
    Bayesian inference for regression on performing Bayesian Normal
    linear regression in metrology to calibrate instruments and evaluate
    inter-laboratory comparisons to determine fundamental constants.

Why is it important? The measurement errors are assumed to be additive,
independent and identically distributed according to a Gaussian
distribution with mean zero and variance σ2, which is usually unknown.
Regression use in metrology is often applied to calibrate instruments,
evaluate inter-laboratory comparisons or determine fundamental
constants, but a regression model cannot be uniquely formulated as a
measurement function, and the Guide to the Expression of Uncertainty in
Measurement (GUM) and its supplements are not applicable directly.
Bayesian inference has the advantage of accounting for additional a
priori information, which typically robustifies analyses.

How is it solved? – methods These three steps (prior elicitation,
posterior calculation, and robustness to prior uncertainty and model
adequacy) and model assumptions are critical to Bayesian inference. In
Bayesian inference, all unknowns—observables (data) as well as
unobservables (parameters and auxiliary variables) considered to be
random are assigned probability distributions to summarize the available
information, and it updates prior knowledge about the unobservables with
information about them contained in the data.The prior distribution and
likelihood function are parts of a Bayesian analysis and it can be
provided by simple graphical displays, by sensitivity analyses or model
checking. For Normal linear regression problems (1), a convenient family
for a prior distribution for θ and σ2 is the Normal inverse Gamma (NIG)
distribution to a posterior from the same family of (NIG) distributions
or (2) alternative families of prior distributions, hierarchical priors
which assign an additional layer of distributions to uncertain prior
parameters or non-para- metric priors may be considered. Graphical
display options of prior and posterior distributions enhance the
elicitation and interpretation process, respectively. • The NIG prior -
if the variance σ2 of observations is known is a conjugate prior
distribution • Vague or non-informative prior distributions can be
derived from the NIG prior Bayesian inference is influenced by
uncertainty in the transformation of prior knowledge to prior
distributions, in the assumptions of the statistical model, and mistakes
in data acquisition all influence the inference.

Results/limitations, if any. The knowledge from related previous
experiments (Normal inverse Gamma distributions) allow for analytic
posterior calculations of many quantities of interest. @Klauenberg2015

5.  Bayesian linear regression What is the goal of the paper? The goal
    of this article is therefore to develop a Bayesian model in which a
    linear regression analysis on current data is augmented with the
    reported regression coefficients (and standard errors) of previous
    studies. The study developed and conducted test a formal method for
    augmenting data in linear regression analyses with previous studies
    including both exchangeable and unexchangable.

Why is it important? Due to the frequent combination of multiple testing
with relatively low statistical power, is problematic in the framework
of null hypothesis significance testing. Linear regression analyses
performed do not account for the published results their summary
statistics) from similar previous studies. The results from previous
studies are source of relevant and readily available information and
ignoring this information affects both the stability and the precision
of the parameter estimates report low than they could have been, and the
conclusions that can be drawn are less certain and more likely to be
affected by sampling variation. Multiple linear regression, includes
separate significance tests for all regression coefficients. Combined
with rather modest sample sizes, this makes it likely for different
studies to find different sets of statistically significant predictors
and to address the use of larger samples, is not realistic.

How is it solved? – methods Bayesian linear regression accommodates
prior knowledge, overcoming the absence of these formal studies from the
literature. Bayesian linear regression handle the issues of increasing
the sample size and to augment the data of a new study with previous
results (regression coefficients and standard errors) from similar
studies was an alternative. It solved the issue of univariate case issue
and also on combining evidence restricted to specific predictors from
different linear regression analysis (as in meta-analysis). It was a
better method to resolve the issue of simultaneously combining multiple
regression parameters per study, separately that ignored the relation
between the regression coefficients. To construct informative priors
using historical data from the previous studies (using the data) was not
be possible in practice, Bayesian linear regression developed a model
and included reported summary statistics from previous studies and
provided a more acceptable solution when data from previous studies are
not (realistically) obtainable.Categorized the model into - 1.
Exchangable- when the current data and previous studies all have the
same set of predictors. 2. Unexchangable – when the predictors were
different Bayesian linear regression – to yield the posterior density of
the model parameters, which reflects the updated knowledge about the
model parameters after having observed the data, steps mentioned are- •
To calculate the probability density function for the data given the
unknown model parameters; taken as a function of those model parameters,
this is referred to as the likelihood function. • The second part is the
prior density function of the model parameters, which quantifies what is
assumed to be known about the model parameters prior to observing the
data. Study applied Standard multiple linear regression model, with the
integration of the prior the to obtain joint posterior density using
Gibbs sampler, an Ordinary Least Squares linear regression was then
applied to each of these samples to obtain the estimated regression
coefficients B and the corresponding standard errors S. And a
hierarchical version of the replication model was developed for
situations where studies are not exchangeable.

Results/limitations, if any. • Incorporating the results of previous
studies in a linear regression on new data does yield a significant
better parameter estimate with an adequate approximation of using the
actual data of those previous studies. • About how much would be gained
in comparison to using just the new data, and how large would the
difference be with the ideal situations in which data from previous
studies were available- it resulted in encouraging performance. •
Performance of the two versions (exchangeable and unexchangeable) of the
replication model were consistently superior to using current data
alone. • It can thus be concluded that the model developed in this
article offers the possibility of obtaining significantly better
parameter estimates in a linear regression setting without needing to
expend a prohibitive amount of time and energy trying to obtain data
from the previous studies. • Hierarchical version (unexchangeable) of
the model offers the advantage of being able to address questions about
differences between studies and thus allows for explicit testing of the
exchangeability assumption.

Limitations • The restriction that all studies have to have the same set
of predictors. • A problem would arise when the predictor variables were
correlated. @DeLeeuw2012a

6.  What is the goal of the paper? The develop a proposed models using a
    longitudinal follow-up cohort study to predict the risk of incident
    cardiovascular disease by incorporating demographic features
    (basic), six metabolic syndrome components (metabolic score) and
    conventional risk factors (enhanced model). The study on
    participants free of CVD at baseline, followed up over five years,
    used Bayesian clinical reasoning model to diagnose new CVD cases.
    Why is it important? • Considering early diagnosis and prevention,
    identifying subjects with high risk for cardiovascular disease (CVD)
    is of paramount importance to health interventions. • The limited
    molecular information (costly and unavilabilty) to clinical practice
    look for alternative approaches to efficiently identify high-risk
    subjects using information form routinely-checked biological markers
    before doing these expensive molecular tests . • Framingham Risk
    Score method, tailored for such a purpose is not sufficient because
    of the differences in ethnic groups and areas, varied socio-economic
    status, require the construction of their own models. Heterogeneity
    (variation with geographic, ethnic group, and nation, and different
    characteristics of social contextual network) is often unobservable
    and un-measurable. How is it solved? – methods Subjects enrolled in
    a Keelung Community-based Integrated Screening (KCIS) Program, for
    mass screening (20–79 years) in the Keelung city of Taiwan, followed
    for 5 years to identify incident cancers and chronic diseases
    (cardiovascular disease). The study classified the risk of having
    incident CVD cases or death from CVD by dint of available calculated
    standardized risk score of the MetS components (fasting glucose,
    blood pressure, HDL-C, triglyceride and waist circumference)
    together with conventional risk factors (gender, heredity, smoking,
    alcohol drinking, family history of parent's CVD and betel quid and
    other relevant factors). Emulate a clinician's evaluation process,
    the author used Bayesian clinical reasoning approach in a sequential
    manner to develop three models considering regression coefficients
    of all predictors as normal distribution for individual risk
    prediction allowing for uncertainty of clinical weights. The
    credible intervals of predicted risk estimates were obtained by
    averaging out. The individual risk is elicited by prior speculation
    (first impression) updated by objective observed data (patient's
    history and laboratory findings). In Bayesian clinical reasoning
    model, the regression coefficients for computing risk score were as
    random variable with certain statistical distribution (e.g. normal
    distribution) rather than a fixed value (traditional risk prediction
    model by frequentist). The updated prior distribution with the
    likelihood based on current data provided into posterior
    distribution to predict the risk for a specific disease. The (basic)
    basic model was developed via logistic regression which used prior
    information constructed on gender, age, age2 and period in further
    analysis. The second (classical) model, the metabolic score model
    (MS model), was established based on six MetS components and then
    the third (enhanced model) incorporated information on smoking,
    drinking, betel-quid, and family history of CVD.
    Results/limitations, if any- • Compared to the basic model and
    classical model, the enhanced model had better performance. • The
    proposed models predicted CVD at individual level by incorporating
    routine information with a sequential Bayesian clinical reasoning
    approach. Patients’s background makes a significant contribution to
    baseline risk. • Even with ecological heterogeneity, the regression
    model adopts individual characteristics to make individual risk
    prediction for the risk for CVD. Limitations – • whether the
    interactions between age, gender, metabolic score and other risk
    factors should be included. • The use of enhanced model should be
    validated through external validation by applying the proposed
    models to new subjects not included in the training the parameters
    of model. @Liu2013
