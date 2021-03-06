# indiahacks-ml-2017
ML challenge for Indiahacks '17  

**Hotstar -- Feature Engineering**

- I collated similar features by observing their correlation with our target variable
  	For eg. "genre_Athletics" , "genre_Badminton" , "genre_Boxing" , "genre_Cricket" , "genre_Football" , "genre_Formula1" , "genre_FormulaE" , "genre_Hockey" , "genre_IndiaVsSa" , "genre_Kabaddi" , "genre_Sport" , "genre_Swimming" , "genre_Table Tennis" , "genre_Tennis" , "genre_Volleyball" were clubbed to form genre_sports

    Separated the time_of_day features into positive_tod, super_positive_tod and remaining_tod, again based on their correlation with "segment"

    I noticed Sunday was a largely important feature, as percentage of day_7 with other days was higher in segment=0 rows.

- Genres: The original watch_time was considered, also ratio of watch_time of one genre compared to total         watch_time was also taken 

- Title Analysis -- Mean, median, sum of each title's watch time was taken
    I also took the ratio of these variables with segment=1 rows against segment=0 rows

    Individual watch time was also compared -- How much was the show watched compared to median of Segment or Overall population

- Cities -- I tried developing some features based on cities, but wasn't getting a lot of improvement. 

**Roadsign -- Feature Engineering**


  Exploration: Understood the dataset by looking at histograms of angle,	height, aspect_ratio of the different subsets.  
  
- Just used some variations of the given features: 
  - `angle on right cam` = `angle on right cam` - 50
  - `angle on rear cam` = `angle on rear cam` - 180
  - `angle on left cam` = `angle on left cam` - 220

- Generated some collective features(mean angle based on combination of detected_cam and target). Got the difference of angle w.r.t these collective means

- Truncated ID -- I thought the truncated ID(ID without last character) might have some effects, so included the count of rows with same truncated_ID(might signify same car having snaps in quick succession).

**Lane Prediction**

 - "lanes_identified": Unique lanes for every road,
 - "compression_factor": ratio of lanes identified and number of lanes,
 - "road_length": road_length,
 - "mean_lane_length": average lane length,
 - "lane_road_ratio": ratio of mean_lane_length and road length,
 - "max_lane_road_ratio": ratio of max lane_length and road length,
 - "max_lane_road_diff_ratio": ratio of diff of max lane_length and road length,
 - "intersecting_count": ratio of lanes which are intersecting geometrically,
 - "intersecting_lane_lines_left": number of intersections on the left side,
 - "middle_lane_road_ratio": ratio of geometric lane with road length,
 - "mean_lane_width_left": Mean of lane width on left side,
 - "mean_lane_width_right": Mean of lane width on right side,
 - "min_diff_road_lane_length": Minimum difference of road length and lane length,
 - "total_road_width": total_road_width,
 - "road_aspect_ratio": road width ratio with road length,
 - "road_category": highway or not,
 - "mean_diff_left_right": mean of difference between distances on right and left side,
 - "min_dist_lane": mean of geographical distances between adjacent lanes,
 - "sum_left_dist": sum of distances on left side,
 - "sum_right_dist": sum of distances on right side
 
 **Movie Recommendation**
 
 - For every user to be predicted, find his maximum occuring language/genre. And serve him movies within that subgroup(language/genre).
 - Item-item based collaborative filtering, on a subset of users(who’ve watched more than ‘n’ number of movies)

Features

 - Watch Ratio: Ratio of movie watched
 - Ratio of watch time with mean watch time of the same language
 - Ratio of watch time with mean watch time of the same genre

All these features were experimented to find the “maximal occuring language/genre”
