# Mistakes Made

### Where my caffeine-fueled hubris collided violently with reality.

##### Mistake One
When I had finished doing the math derivations and had built out the initial dataframe, I felt like nothing could stop me. of course, when my gyro_z calculations had ballooned to 5.000000e-01, NaN, NaN -7.205759e+15, and then NaN forevermore, I was proven that it would not be an easy ride.

I spent 15 minutes afterwards researching np.wrap, how np.gradient calculates the actual result, and then realized that the issue was the dt- which was identical at every value except for the first due to the very humble prepend=0 I added on to it to keep track of the timestep. the whole (np.gradient(heading,dt)) function caused a division by zero error that caused it to go to nowhere and below.

Lesson learned: np.gradient can calculate the difference on its own, just use your time array directly. Remember KISS: Keep it simply, Stupid, no need to already do the difference when np.gradient can calculate the difference.
