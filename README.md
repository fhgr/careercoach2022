# CareerCoach 2022 Dataset

This repository contains the CareerCoach 2022 Dataset introduced in the article:

Weichselbraun, Albert, Waldvogel, Roger, Fraefel, Andreas, van Schie, Alexander and Kuntschik, Philipp. (2022). “Slot Filling for Extracting Reskilling and Upskilling Options from the Web”. Proceedings of the 27th International Conference on Natural Language & Information Systems, Valencia, Spain

# Dataset description

## Dataset partitions
The dataset contains the following two partitions:

1. Partition P1: 
   - size: 169 documents
   - annotations: page segment (classification, start/end index, surface form)
   - supported tasks: T1 (page segment recognition), T2 (page segment classification)
2. Partition P2:
   - size: 75 documents
   - annotations:
     - page segment (classification, start/end index, surface form)
     - identified entities (start/end index, identifier, type (e.g., skill, occupation, topic, position, school, industry, education, degree), key)
   - supported tasks:
     - T1 (page segment recognition)
     - T2 (page segment classification)
     - T3 (entity recognition)
     - T4 (entity classification
     - T5 (entity linking)
     - T6 (slot filling)

## Annotation format

The published `.json` files contain annotations in the following format:

```json
{
 "html": "...",
 "text": "...",  
 "page_segments": {
    "target_groups": [
        {
         "surface_form": "Text of first segment",
         "start": 5,
         "end": 26 
         }
      ],
     "course_contents": [
         {...}
     ]
    },
 "entities": {
    "target_groups": [
        {
         "surface_form": "Entity 1",
         "start": 15,
         "end":22,
	 "key": "https://semanticlab.net/career-coach#458"
         }
      ],
     "course_contents": [
         {...}
     ]
    }
}
```

### Description:

1. `html`: the page's HTML content
2. `text`: the corresponding text representation as obtained by [inscriptis](https://github.com/weblyzard/inscriptis).
3. `page_segments`: a dictionary of classified page segment with keys: `target_groups`, `course_contents`, `prerequisite`, `learning_objectives`, `certficates_and_degrees`. Each page segment contains another dictionary outlining its `surface_form`, `start` and `end` indices.
5. `entities` optional further dictionaries that describe entities identified within the segments.
   - each entity is described by `surface_form`, `start` and `end` indices, `type` and `key`. In addition entities _may_ contain the keys `wikidata`, `wikipedia` and `wikipedia_redirect` which refer to their URL in the corresponding knowledge sources.
   - `type`: indicates the entity class (`skill`, `occupation`, `topic`, `position`, `school`, `industry`, `education`, or `degree`)
   - `key`: unique entity URL within the knowledge graph
