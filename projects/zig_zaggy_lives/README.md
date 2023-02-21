# zig_zaggy_lives

**Background**

This project was born out of a need to understand exactly what happens to a cohort of students, specifically at points in time that are outside of the common landmarks. Universities tend to closely monitor their 4-year and 6-year graduation rates, but not necessarily the “zig-zaggy” paths students might take before reaching that point, if they ever do. 

Understanding these trajectories helps universities to identify pain points in where they may be losing students, and at what point in their college career. 

**Data Pulling**

The first step in this project was data pulling. Data were pulled via SQL from the university’s student information system using a correlated scalar subquery, in which a student’s total earned hours was aggregated across 30 semesters (10 years). This created the base file I worked from.

From there, multiple supplemental data sets were pulled, including graduation information, transfer-out information, and an additional data set related to a student’s earned hours, in order to correct a few edge cases (more on that later).

**Data Wrangling**

Once the data were pulled, an R script was created to 1) format the data sets into the needed structures, and then 2) combine them with the base file to create a final data set that would be fed into the animation.

Establishing the logic behind identifying when students drop out, transfer out, or take a hiatus ended up being a large portion of this project. The methodology used was as follows:

- If a student graduated, that was always given priority.
- If a student had enrollment activity at an external institution, they were considered a transfer-out. Note that this classification is not terminal; a student may transfer out, but may also return to MSU Denver as well. 
- If a student did not graduate, and had no record of enrollment at an external institution, they were considered a drop-out. Also note that when looking at specific cohorts of students, the closer we come to the present, the less reliable the drop-out data becomes, as insufficient time has elapsed to know whether students are potentially on hiatus, or have transferred out.

**Animating**

Finally, work could begin on building the animation. The animation layout was inspired by Nathan Yau’s “A Day in the Life of Americans”. I had never used Javascript before, and so utilized his base code as much as possible to start. By the end of this project, however, the Javascript would look nothing like its original.

Major structural changes from other similar animations found online include a shift away from custom physics functions in favor of working with built-in functionality, a complete rework of the input data (and JS) to function column-wise, rather than row-wise, the ability to perform data-set switching, and the ability to filter down to smaller population subsets. 
