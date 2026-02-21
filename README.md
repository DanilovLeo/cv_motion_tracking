# Optical Flow Motion Analysis

## Variant B: Motion Tracking Module

Analysis of optical flow methods (Lucas-Kanade and Farneback) for video motion tracking.

## Parameters

### Lucas-Kanade (Sparse)
- Max corners: 100
- Quality level: 0.3
- Min distance: 7
- Window size: 15x15
- Max pyramid level: 2
- Frames tracked: 200

### Farneback (Dense)
- Pyramid scale: 0.5
- Pyramid levels: 3
- Window size: 15
- Iterations: 3
- Poly n: 5
- Poly sigma: 1.2
- Thresholds tested: 2.0, 0.9

## Results

### Lucas-Kanade
- Initial points: 100
- Final points: 67
- Point loss: 33%
- Gradual degradation with sharp drop at frames 100-140 (occlusions/objects leaving frame)

### Farneback
**Threshold 2.0:**
- Motion pixels: 1.6%
- Fragments: 13

**Threshold 0.9:**
- Motion pixels: 9.5%
- Fragments: 41

### Key Observations

**LK Strengths:**
- Stable long-term tracking
- Clear trajectory visualization
- Predictable point loss behavior

**LK Weaknesses:**
- Loses points over time (33% over 200 frames)
- Requires good texture/features

**Farneback Strengths:**
- Complete motion field coverage
- Detects all moving regions

**Farneback Weaknesses:**
- High fragmentation (41 regions at threshold 0.9)
- Threshold-sensitive: lower threshold captures more motion but increases noise
- Cannot distinguish real motion from noise without post-processing

## When to Use

**Use Lucas-Kanade when:**
- Tracking specific objects/features
- Speed is critical
- Have distinct keypoints

**Use Farneback when:**
- Need full scene motion analysis
- Detecting all moving objects
- Motion segmentation required (with post-processing)

## Conclusion

For this video (crowd motion), LK performed better due to stable tracking and clear trajectories. Farneback showed high fragmentation, demonstrating its sensitivity to noise and need for careful threshold tuning.
