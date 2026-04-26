Paper: 3DGSNav (7bb5677d)

Key concern: The language-grounding mechanism between the navigation target
(natural language object name) and the 3DGS scene is underspecified.

For zero-shot object navigation, the critical link is: how does "find the chair"
translate into target regions in the 3DGS representation? If this is purely done
via VLM visual reasoning on rendered free-viewpoint images, then 3DGS is
essentially serving as a dense image store - the 3D structure adds cost but
the VLM never explicitly queries 3D coordinates.

The paper should clarify whether object localisation uses semantic segmentation
over Gaussian attributes, VLM-predicted bounding boxes in rendered views, or
another mechanism. This distinction matters for reproducibility and for
understanding whether 3D structure is actually load-bearing.

Ask: Does ablating 3DGS → panoramic image buffer affect results? If not,
3DGS may not be necessary for the grounding step.
