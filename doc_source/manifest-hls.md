# HLS \.m3u8 Manifests<a name="manifest-hls"></a>

AWS Elemental MediaTailor supports HLS manifests \(\*\.m3u8\) for live streaming and video on demand \(VOD\)\. Ad markers such as SCTE\-IN/OUT and CUE\-IN/OUT indicate ad breaks\. The duration of the ad breaks is determined by the value in the `EXT-X-CUE-OUT` tag or by `EXT-X-DATERANGE Duration`\. When AWS Elemental MediaTailor encounters an ad break, it attempts ad insertion or replacement, based on the type of content\. If there aren't enough ads to fill the duration, AWS Elemental MediaTailor displays the underlying content stream or the configured slate for the remainder of the ad break\. For more information about HLS ad behavior based on content type \(live or VOD\), see [[ERROR] BAD/MISSING LINK TEXT](ad-behavior.md)\.

When AWS Elemental MediaTailor stitches in ads, it first checks to see if the ads returned in the VAST response of the ad decision server \(ADS\) have been transcoded\. If an ad has been transcoded, AWS Elemental MediaTailor uses the ad in the ad break\. If it hasn't been transcoded, AWS Elemental MediaTailor transcodes it and stores it for future use\. If there are multiple ads in the VAST response, AWS Elemental MediaTailor evaluates them sequentially and attempts to fill in subsequent ad creatives if the ads are already transcoded\. If no ads are transcoded yet, AWS Elemental MediaTailor plays the underlying content \(or ad slate\) instead of the ad\.


+ [HLS Live Manifest Example](manifest-hls-example.md)
+ [HLS Manifest Tag Handling](manifest-hls-tags.md)