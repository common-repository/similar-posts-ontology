=== Similar Posts Ontology ===
Contributors: cfischer83
Tags: similar, related, posts, articles, content, associated, taxonomy, category, tags
Requires at least: 4.0.0
Tested up to: 6.5
Stable tag: 2.1
License: GPLv2 or later
License URI: http://www.gnu.org/licenses/gpl-2.0.html

Show a list of related posts that are similar to another post.

== Description ==

Does your website utilize categories and tags? Does it use custom taxonomies? If so, this plugin will find similar content
based on all your taxonomies. There are two ways to show related posts within your page.

* The first way to show related content on your post is to use the widget provided. This only works when is_single() is true
* The second way to show similar content on your site is to use the pk_related_return($post->ID); function which can be 
called programmatically anywhere you wish!

The Widget included with this plugin gives you the option to limit the amount of posts; it allows you to determine which
fields to show: Featured Image, Author, Date, and Excerpt (Title is required);  it allows you to determine which 
variant of the featured image to show: thumbnail, medium, large, or full. As of version 2.0, you can now decide whether the
'similar posts' sorting prefers posts that are newer or posts that were created closer to the date of the post you're
viewing.

If you find the Widget doesn't meet your needs or is too limiting, you can call the functionality programmatically using
this function:

`pk_related_return($post->ID, $args);`

Where $post->ID is the ID of the post for which you are wanting to show related articles.

The $args parameter is an array with the following values available to you (more coming soon):

* posts_per_page (int defaults to 5)
* thumbnail_size (string consisting of one of these values: "thumbnail", "medium", "large", "full". Defaults to thumbnail).
* sort_prefer	   (string consisting of one of these values: "newest", "closest". Defaults to newest).

An example might be:

`<?php
$args = array (
	'posts_per_page' => 6,
	'thumbnail_size' => 'medium',
	'sort_prefer' => 'closest'
);
`

The return value of pk_related_return is an array of objects that includes most of the fields within WordPress's posts
table plus permalink and featured image.

Future Additions:

Allow the user to specify only certain content types (posts, pages, custom) in a request. This would allow you to specify
only products get returned, or only blog posts. This would only be an issue if content types share taxonomies.

== Installation ==

1. Upload `similar-posts-ontology` to the `/wp-content/plugins/` directory
2. Activate the plugin through the 'Plugins' menu in WordPress
3. If you want the widget, go to 'Appearance' -> 'Widgets' and look for Similar Posts Ontology widget. If you prefer to call programmatically, use the pk_related_return function in your theme.

== Screenshots ==

1. You can define how your widget looks from the widget admin/edit screen.
2. You can have it output as a simple list like other, typical side-bar widgets.
3. Or you can add fields and your own styles to really make it stand out (this example is found at www.bluecrayon.net)

== Frequently Asked Questions ==

= How does this plugin work? =

There are two aspects to it. First, it finds all similarly tagged, categorized, and otherwise taxonomically created content
on your site, then sorts it by what has the most similarities. Second, if there is a tie between two posts it will give
the edge to the newest content, or content posted closer to the time your current post was posted, depending how you configure it.

= Why Ontology? What's an Ontology? =

Ontology is the study of the nature of 'being'. This plugin uses the ontological philosophy of determining an entities 
placement within its own 'type' by studying the entities relationships.

= Why am I not seeing any content when I install this? =

You can use this in two ways. Either by calling pk_related_return() in your theme or by placing the widget on your site.
If you are using the widget, remember that it only works on any "single" page (where is_single() would return true). The
pk_related_return() can theoretically work anywhere as long as you provide a proper post ID. Try var_dump() with 
pk_related_return() and look at the description for proper usage of this function.

= Why are my results coming back with weird content that I wouldn't expect? =

This issue may be your taxonomies. The content for which you're trying to find related content needs to have tags, 
categories, and/or custom taxonomies. Also, to properly find your content, tags/categories/taxonomies must be used on
the *related* content as well. The more you intentionally use your tags and categories, the better your results set will be.

== Changelog ==

= 2.1 =
*Release Date - July 31st, 2016*
* Include some base styles to look better with common theme conventions
* Fixed bug where author URL was broken
* Tested up to 4.6

= 2.0 =
*Release Date - August 15th, 2015*
* Optimized query to allow for the option of specifying sorting preferences.

= 1.0.1 =
*Release Date - January 11th, 2015*
* Made the widget include HTML and classes that are best practice.

= 1.0 =
*Release Date - January 10th, 2015*
* First Version
