# Conclusions

A summary of any notable findings: to be updated as I go.

## From main analysis

### Facebook Congress
- Female posters have longer posts than male posters
- Female posters may use slightly longer sentences than male posters
- Female posters use hedges more often than male posters (4.5% vs. 2.4%)

### Facebook Wiki
- Male posters have longer posts than female posters
- Male posters use hedges more often than female posters (3.3% vs. 1.8%)

### Fitocracy
- Female posters may have longer posts than male posters
- Responses to female posters are a little longer than responses to male posters
- Female responders have longer responses when they are responding to a female poster than when they are respondng to a male poster
- Female responders use longer sentences than male responders
- Male responders use slightly longer sentences when responding to a male poster than when responding to a female poster
- Female responders use slightly longer sentences when responding to a female poster than when responding to a male poster
- Male and female posters use hedges about equally, but male responders use hedges more often than female responders (3.2% vs. 2.4%)

### Reddit
- Female posters have longer posts than male posters
- Responses to female posters are a little longer than responses to male posters
- Female responders have longer responses than male responders
- Both male and female responders have longer responses when responding to female posters than when responding to male posters
- Female posters use hedges more often than male posters (11.1% vs. 8.8%) and female responders use hedges more often than male responders (13.1% vs. 9.8%)

### TED
- Responses to male speakers may be slightly longer than responses to female speakers

## From machine learning

### Predict gender of any post/response
- Baseline: 60% male. We need at least 60% accuracy with our model.
- Using Naive Bayes, I achieved 70.6% accuracy

### Predict gender of poster and responder given response text
- Baseline: 32.6% of posts were male poster/male responder. This is a hard task - can we predict information about both people when only looking at the response?
- Using Naive Bayes, I achieved 44.8% accuracy. This is obviously not good, but considering the difficulty of the task, and the fact that it's 12 points higher than our baseline, it's definitely not a failure.

### Predict gender of poster given response text
- Baseline: 59.8% of responses were responding to a male poster.
- Using Naive Bayes, I achieved 62.4% accuracy. This is a very small improvement from the baseline and I can assume that this task is very difficult.

