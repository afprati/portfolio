---
title: "Topic Modeling State of the Union Speeches"
author: "Annamaria Prati"
date: "June 2016"
output: html_document
---

In an election year, when we consider what challenges the next president will inevitably face, it could be helpful to look at recent presidencies to see if there are consistent themes for a president's concerns and goals.  One rather succinct event where these themes are outlined is in the annual State of the Union addresses (often referred to as SOTUs).  Theoretically, if one goes too far back in time, the world stages might no be comparable, and the themes might not be as meaningful.  Therefore, as a starting point, I considered topic modeling SOTUs from the end of the Cold War (which I am dating as 1990) to today. I got the text from the SOTUs from the American Presidency Project at UC Santa Barbara, and included all SOTUs from 1990 through 2016 (excluding  speeches that the project flagged as not "true" SOTU speeches at the beginning of a new administration, i.e. Clinton's 1993 speech, Bush's 2001 speech, and Obama's 2009 speech) for a total of 24 speeches.

First, I set up the corpus.  Note that I removed stoppage words, but did not remove low frequency words due to the relatively small corpus, and did not stem the words since it seemed to have minimal impact (for example, stemming considers "american" and "americans" to be of the same stem, but "american" and "america" were kept separate).

Now I am ready to analyze the speeches. What are the top 25 words in the SOTUs? Unsurprisingly, words related to "America" are the most common, as well as words related to the economy and jobs, foreign affairs, and dpossibly domestic government.  It is interesting that the word "help" is used so frequently, and it is unclear what is meant by that.  For a closer look, I looked at the original corpus to look at the words in context. As might be expected, "help" is used in a wide variety of contexts, from foreign policy ("help Ukraine defend its democracy" (2016)) to philanthropy ("help one hungry child" (1991)) to the economy ("help one million young Americans work" (1996)) to generally inspirational ("help us reach that goal" (2005)).

Returning to the original question, what are the consistent issues that a new president would have to face?  Qualitatively from the world cloud, the economy is a looming issue, along with world affairs, domestic governance, and families.  More quantitatively, we can examine the themes through a topic model.

Of the top 25 topics, many include some variant of "America", unsurprising since these are SOTUs. Several seem to be related to the economy and jobs (using terms like "work" and "job"), and several others seem to be related to national security and foreign policy, including the war in Iraq but not the war in Afghanistan (using terms like "weapon," "nation," "world," "iraq," and "secure").  

To conclude, based on themes from the SOTU addresses since the Cold War, the future president will have to address jobs and the economy  and then issues of national security and war.  Under both subject headings, the future president will need to support American pride and nationalism by rhetorically reaffirming America's place in the world order and the importance of Americans' relationships to each other.