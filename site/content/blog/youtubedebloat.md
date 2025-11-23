+++
author = "Tiffany"
title = "Debloating the Youtube UI"
date = "2025-11-23"
description = "Youtube Debloat"
tags = [
    "websites"
]
+++

Some filters for ublock origin to make the youtube ui more minimal and less distracting. I found most of these on r/ublockorigin, and by using the point-and-click feature.

Removes shorts, feeds/recommendations, homepage, and the weird trending searches.

    ! Hide home page

    youtube.com##[page-subtype="home"]

    www.youtube.com###guide [title="Home"], .ytd-mini-guide-entry-renderer[title="Home"]

    ! YT Homepage - Hide the Shorts section

    youtube.com##[is-shorts]

    ! YT Menu - Hide the Shorts button

    www.youtube.com###guide [title="Shorts"], .ytd-mini-guide-entry-renderer[title="Shorts"]

    ! YT Search - Hide Shorts

    www.youtube.com##ytd-search ytd-video-renderer [overlay-style="SHORTS"]:upward(ytd-video-renderer)

    ! YT Search and Channels - Hide the Shorts sections

    www.youtube.com##ytd-reel-shelf-renderer

    ! YT Channels - Hide the Shorts tab

    www.youtube.com##ytd-browse[page-subtype="channels"] [role="tab"]:nth-of-type(3):has-text(Shorts)

    ! YT Subscriptions - Hide Shorts - Grid View

    www.youtube.com##ytd-browse[page-subtype="subscriptions"] ytd-grid-video-renderer [overlay-style="SHORTS"]:upward(ytd-grid-video-renderer)

    ! YT Subscriptions - Hide Shorts - List View

    www.youtube.com##ytd-browse[page-subtype="subscriptions"] ytd-video-renderer [overlay-style="SHORTS"]:upward(ytd-item-section-renderer)

    ! YT Sidebar - Hide Shorts

    www.youtube.com###related ytd-compact-video-renderer [overlay-style="SHORTS"]:upward(ytd-compact-video-renderer)

    ! YT Search - keep videos and channels

    youtube.com##ytd-search ytd-item-section-renderer>#contents>:not(ytd-video-renderer,ytd-channel-renderer),ytd-secondary-search-container-renderer

    ! Remove empty spaces in grid

    www.youtube.com##ytd-rich-grid-row,#contents.ytd-rich-grid-row:style(display: contents !important)

    ! Hide all videos containing the phrase "#shorts"

    www.youtube.com##ytd-grid-video-renderer:has(#video-title:has-text(/(^| )#Shorts?( |$)/i))

    www.youtube.com##ytd-rich-item-renderer:has(#video-title:has-text(/(^| )#Shorts?( |$)/i))

    ! Hide all videos with the shorts indicator on the thumbnail

    www.youtube.com##ytd-grid-video-renderer:has([overlay-style="SHORTS"])

    www.youtube.com##ytd-rich-item-renderer:has([overlay-style="SHORTS"])

    www.youtube.com##ytd-video-renderer:has([overlay-style="SHORTS"])

    www.youtube.com##ytd-item-section-renderer.ytd-section-list-renderer[page-subtype="subscriptions"]:has(ytd-video-renderer:has([overlay-style="SHORTS"]))

    ! Hide shorts button in sidebar

    www.youtube.com##ytd-guide-entry-renderer:has(yt-formatted-string:has-text(/^Shorts$/i))

    ! Tablet resolution

    www.youtube.com##ytd-mini-guide-entry-renderer:has(.title:has-text(/^Shorts$/i))

    ! Hide shorts sections except on history page

    www.youtube.com##:matches-path(/^(?!\/feed\/history).*$/)ytd-rich-section-renderer:has(#title:has-text(/(^| )Shorts( |$)/i))

    www.youtube.com##:matches-path(/^(?!\/feed\/history).*$/)ytd-reel-shelf-renderer:has(.ytd-reel-shelf-renderer:has-text(/(^| )Shorts( |$)/i))

    ! Hide shorts tab on channel pages`

    ! Old style

    www.youtube.com##tp-yt-paper-tab:has(.tp-yt-paper-tab:has-text(Shorts))

    ! New style (2023-10)

    www.youtube.com##yt-tab-shape:has-text(/^Shorts$/)

    ! Hide short remixes in video descriptions and in suggestions beside the comments

    www.youtube.com##ytd-reel-shelf-renderer:has(#title:has-text(/(^| )Shorts.?Remix.*$/i))

    ! Hide shorts category on homepage and search pages

    www.youtube.com##yt-chip-cloud-chip-renderer:has(yt-formatted-string:has-text(/^Shorts$/i))

    ! Hide shorts container

    www.youtube.com###shorts-container

    ! YT Home - Hide videos based on channel names

    youtube.com##ytd-browse[page-subtype="home"] ytd-rich-item-renderer:has(#avatar-link:is([title="Full Channel Name"], [title*="Partial Channel Name"], [title="Case Insensitive Channel Name"i]))

    ! YT Home - Hide videos based on their titles

    youtube.com##ytd-browse[page-subtype="home"] ytd-rich-item-renderer:has(#video-title-link:is([title*="Partial Match"], [title*="Case-Insensitive Partial Match"i], [title~="Space-separated-aka-Whole-word-match"]))

    ! YT Home - No Videos

    www.youtube.com##ytd-browse[page-subtype="home"]

    ! YT Videos - No Sidebar

    www.youtube.com##ytd-watch-flexy #secondary

    ! YT Videos - Sidebar Without Recommendations

    www.youtube.com##ytd-watch-flexy #secondary

    ! Hide search tag scroll container

    www.youtube.com###container > .yt-chip-cloud-renderer.style-scope

    ! Hide explore section from sidebar

    www.youtube.com##ytd-guide-section-renderer.ytd-guide-renderer.style-scope:nth-of-type(3)

    ! Hide trending searches
    ||suggestqueries*.youtube.com/complete/search*&q=&$xhr


I use youtube signed out in a private window so this is some other stuff I remove. I find comments distracting and not useful so I removed that as well.

    ! extra stuff I deleted like side menu, guide, and icons on top
    www.youtube.com###guide-button
    www.youtube.com##ytd-mini-guide-renderer.ytd-app.style-scope
    www.youtube.com###icon > .yt-icon-button.style-scope
    www.youtube.com###buttons > ytd-button-renderer.ytd-masthead.style-scope
    www.youtube.com##ytd-topbar-menu-button-renderer.ytd-masthead.style-scope
    www.youtube.com###logo
    www.youtube.com###guide

    ! Hide comments
    www.youtube.com###comments > .ytd-comments.style-scope

    ! Hide video menu items (likes, share, join, etc)
    www.youtube.com###menu > .ytd-watch-metadata.style-scope
    www.youtube.com###subscribe-button-shape
    www.youtube.com##.smartimation__content > ytd-button-renderer > yt-button-shape