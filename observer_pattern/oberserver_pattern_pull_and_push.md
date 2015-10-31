# Observer Pattern Pull And Push

In fact, there are two mechanisms for observer pattern:

* Push

Subject "push" informations, for exemple a String, directly to observers.

* Pull

Subject notify observers directly with Subject instance, so observers could "pull" whatever they want from Subject instance.

The exemple in the last page is a "Pull"

# Push VS Pull

Push supposes that Subject knows well what observers want. Pull doesn't know it, so Pull passes its own to observers to let them choose the informations they want.

Push may make it difficult to reuse observers, because observers' update () method is based on parameters, it might not take into account the usages which are not taken into account. This means that when new situations arise, it needs to provide a new update() method, or simply to re-implement the observer. But with Pull, it would not cause such a situation, because update () method has Subject itself as input which has almost maximum data collection, and basically meet the needs of a variety of situations.
