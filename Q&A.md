# What is the purpose of using multiple anchors per feature map cell?
- This enables the network to predict multiple objects of different sizes per image location. Having multiple anchors allows the network to generalize better as it may happen that if we want to detect faces then they may have a square-shaped bounding box in general, whereas
something like a mobile phone may normally have a rectangular bounding box. 
- Hence multiple anchors help the network in detecting objects of various shapes and sizes much more accurately 


# Does this problem require multiple anchors? Please justify your answer?
- Given how most of the cigarette packs in the world are rectangular in shape a single aspect ratio, with boxes of multiple scales, pertaining to rectangular shape should suffice (however multiple aspect ratios should be chosen so that packs or various widths and heights can be easily detected).
- Using multiple anchor boxes of various aspect ratios and scales can thus help the network detect packs of varying sizes and shapes, and hence I think that this problem requires multiple anchor boxes in order to give much better accuracy.
- Also, having boxes of boxes of multiple scales will help the network detect smaller objects as well as larger objects with ease
