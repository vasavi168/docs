# Smart Link

URL shortening is a technique in which a URL may be made substantially shorter in length and still direct to the required page. This is achieved by using an HTTP Redirect on a domain name that is short, which links to the web page that has a long URL

This is especially convenient for messaging technologies which severely limit the number of characters that may be used in a message.

Smart url also tracks the traffic ie the number of visits to the domain and further advanced analytics as to who (mobile number) visited the page.

#### Customizing the redirection of Smart URL

Use a single short URL in your SMS campaign and based on your customer's device details route them to different domain of your's.

Below are the replaceable parameters that can be used along with the URL to extract customer device/IP details

|Name|Description|Example|
|--- |--- |--- |
|client_ip|IP from which the URL was accessed|156.151.23.65|
|host|Domain name of the URL|Example.com|
|user_agent|User agent used by the URL|Mozilla/5.0 (iPad; U; CPU OS 3_2_1 like Mac OS X; en-us) AppleWebKit/531.21.10|
|browser|Browser in which the URL was accessed|msie|
|browser_version|Version of the browser in which the URL was accessed|11.0|
|browser_lang|Language of the operating system in which the URL was accessed|English|
|browser_engine|Browser engine in which the URL was accessed|Trident|
|platform|Operating system of the device in which the URL was accessed|androidos|
|platform_name|code of the OS from where the URL was accessed|(AN) for Android|
|platform_version|Version of the operating system of the device in which the URL was accessed|5.0|
|device_type|Type of device in which the URL was accessed|phone|
|device_brand|Brand of the device in which the URL was accessed|Motorola|
|device_version|Version number of the device in which the URL was accessed|XT1068|
|device_model|Model name of the device in which the URL was accessed|HTC Dream|
|touch_enabled|If or not the device from where the URL was accessed is touch enabled or not|yes|
|country_code|Country from where the URL was accessed|IN|
|country|Country from where the URL was accessed|india|
|region|State from where the URL was accessed|Karnataka|
|city|City from where the URL was accessed|Bangalore|
|created_at|requested time in unixtimestamp|1426243175|
|mobile|Short URL recepient mobile number|9999999999|

## WebHook

The concept of a WebHook is simple. A WebHook is an HTTP callback: an HTTP GET that occurs when something happens; a simple event-notification via HTTP GET.

We will send `curl` request to your server with above replacable variables. You can store those details in your crm or perform any action against it.
