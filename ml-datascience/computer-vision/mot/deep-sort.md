# Deep SORT

The improvements w.r.t. the [sort.md](sort.md "mention") algorithm:

* Incorporates association metrics based on appearance features.
* Incorporates ID assignment to track individual objects across frames.

<figure><img src="../../../.gitbook/assets/image (126).png" alt=""><figcaption></figcaption></figure>

## Steps

1. Detection and feature extraction
   * Using any detector
2. Apply Kalman filter
   * For the state prediction
   * Given the current position, velocity, and acceleration
   * Predicts the state of each object given the motion dynamics
3. Association:
   * Hungarian algorithm performs matching based on a cost matrix that considers:
     * **Mahalanobis** distance between bboxes (current and Kalman filters' prediction)
     * **Cosine distance** for appearance similarity
4. Track management (algorithm heuristics)
   * It confirms a track when is detected after several consecutive frames.
   * Age parameter to remove old tracks no longer existing.
