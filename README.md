# Strava Suffer Score
## Decoding the Algorithm
I’ve purchased a Suunto Ambit 2 few days ago, mainly because I was looking for something new after two years, and thousands of kilometres, with my faithful Polar RC3 (which still rocks as the first day).
From a Computer Science student point of view, the chance to build apps for and upload them on it, is one of the main feature that made me decided to go for it. As well as, it is the most used GPS watch in the ultra-marathon scene.

I’m also a big fan of Strava, for what it concern the social part of the sport. So, my main thought was: why not to try to decode the Strava Suffer Score algorithm in order to make it an app?

At the end these are the approximative results:

- Z1: 25 point/hour
- Z2: 60 point/hour
- Z3: 115 point/hour
- Z4: 250 point/hour
- Z5: 300 point/hour

## Making of the Suunto App
And here’s the final code for the Movescount App Zone editor.

```
RESULT = SCORE;
if(SUUNTO_HR >= SUUNTO_USER_REST_HR && SUUNTO_HR <= 60*SUUNTO_USER_MAX_HR/100) {
	SCORE = SCORE + 25/3600;
} else {
	if(SUUNTO_HR > 60*SUUNTO_USER_MAX_HR/100 && SUUNTO_HR <= 70*SUUNTO_USER_MAX_HR/100) {
		SCORE = SCORE + 60/3600;
	} else {
		if(SUUNTO_HR > 70*SUUNTO_USER_MAX_HR/100 && SUUNTO_HR <= 80*SUUNTO_USER_MAX_HR/100) {
			SCORE = SCORE + 115/3600;
		} else {
			if(SUUNTO_HR > 80*SUUNTO_USER_MAX_HR/100 && SUUNTO_HR < 90*SUUNTO_USER_MAX_HR/100) {
				SCORE = SCORE + 250/3600;
			} else {
				SCORE = SCORE + 300/3600;
			}
		}
	}
}
```