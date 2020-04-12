# Wordpress Cooked Plugin SEO Optimization Fix

1. Go to plugin editor (wordpress menu > plugins > edit plugins)

2. Select "Cooked" plugin from left side on page ("Select plugin to edit dropdown)
<img src="https://user-images.githubusercontent.com/19264860/79079511-3a5bc000-7d18-11ea-8f33-456fa792dcbd.png" />

3. Find "class.cooked-seo.php" file in plugin files list under "includes" folder
<img src="https://user-images.githubusercontent.com/19264860/79079537-69723180-7d18-11ea-9bf0-af060921e3d6.png" />

4. Finally add these rows in to "$schema_array" variable in "schema_values" function. (php file added)

All of these optional tags for Google but i think "keywords" and "video" tags are important.
``` php
'keywords' => ( isset($recipe['title']) ? $recipe['title'] : '' )
```

``` php
'recipeCuisine' => ''
```		

``` php
'aggregateRating' => ''
```

``` php
'video' => array (
				'@type' => 'VideoObject',
				'name' => ( isset($recipe['title']) ? $recipe['title'] : '' ),
				'description' => ( isset($recipe['seo_description']) && $recipe['seo_description'] ? $recipe['seo_description'] : ( isset($recipe['excerpt']) && $recipe['excerpt'] ? $recipe['excerpt'] : ( isset($recipe['title']) ? $recipe['title'] : '' ) ) ),
				'contentUrl' => ( isset($recipe['gallery']['video_url']) && $recipe['gallery']['video_url'] ? $recipe['gallery']['video_url'] : '' ),
				'thumbnailUrl' => $recipe_thumbnail,
				'uploadDate' => get_the_date( 'Y-m-d', $recipe['id'] ),
			)
```
