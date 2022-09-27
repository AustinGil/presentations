what it takes to make a div

Magic schoolbus theme

3 chapters
- Writing Code (VS Code into .vue file -> Save -> Transpile -> Git push)
- Deploying (Git actions -> build -> transpile -> Docker -> Registry -> Tigger deploy)
- Responding to request (url -> Browser -> OS -> Wifi -> Router -> Modem -> ISP -> NS -> DNS -> CDN -> IP -> TCP handshake -> TLS handshake -> HTTP request -> Proxy -> web server -> cache -> valid HTTP response -> download html -> download CSS -> download JS -> document.createElement('div'))

In the good old days, when kids would play outside and when you scraped your knees, your father would literally rub some dirt in it.
When you wanted to make a div, you'd hit the power button with your big toe, crack open Notepad++, yell at your mom to get off the phone, dial up that sweet, sweet internet connection, and FTP that sucker over. Then someone would type in your URL, (insert router -> modem -> ISP) the browser would find the Nameserver, follow that to query the DNS record, find the IP address, TCP handshake: Your browser opened a connection with that IP address, TLS handshake: Your browser also set up encryption between a Cloudflare web server and your device so that attackers cannot read the data packets that travel between those two endpoints.
HTTP request: Your browser requested the content that appears on this webpage.
HTTP response: Cloudflare's server transmitted the content in the form of HTML, CSS, and JavaScript code, broken up into a series of data packets. Once your device received the packets and verified it had received all of them, your browser interpreted the HTML, CSS, and JavaScript code contained in the packets to render this article about how the Internet works. The whole process took only a second or two, load the Apache server, and download that index.html file.

DNS
A user types ‘example.com’ into a web browser and the query travels into the Internet and is received by a DNS recursive resolver.
The resolver then queries a DNS root nameserver (.).
The root server then responds to the resolver with the address of a Top Level Domain (TLD) DNS server (such as .com or .net), which stores the information for its domains. When searching for example.com, our request is pointed toward the .com TLD.
The resolver then makes a request to the .com TLD.
The TLD server then responds with the IP address of the domain’s nameserver, example.com.
Lastly, the recursive resolver sends a query to the domain’s nameserver.
The IP address for example.com is then returned to the resolver from the nameserver.
The DNS resolver then responds to the web browser with the IP address of the domain requested initially.
Once the 8 steps of the DNS lookup have returned the IP address for example.com, the browser is able to make the request for the web page:

The browser makes a HTTP request to the IP address.
The server at that IP returns the webpage to be rendered in the browser (step 10).

What is DNS caching? Where does DNS caching occur?
- Browser DNS caching
- Operating system (OS) level DNS caching
- Router

TCP over IP
TCP handshake: First, the source send an SYN “initial request” packet to the target server in order to start the dialogue. Then the target server then sends a SYN-ACK packet to agree to the process. Lastly, the source sends an ACK packet to the target to confirm the process, after which the message contents can be sent. 


TLS (or SSL)
TLS handshake: During the course of a TLS handshake, the client and server together will do the following:
- Specify which version of TLS (TLS 1.0, 1.2, 1.3, etc.) they will use
- Decide on which cipher suites (see below) they will use
- Authenticate the identity of the server via the server’s public key and the SSL certificate authority’s digital signature
- Generate session keys in order to use symmetric encryption after the handshake is complete

Critical rendering path
- Constructing the DOM Tree (DOM = Object representation of the fully parsed HTML page)
- Constructing the CSSOM Tree (CSSOM = Object representation of the styles associated with the DOM)
- Running JavaScript
- Creating the Render Tree (Render Tree is a combination of both the DOM and CSSOM for RENDERED nodes)
- Generating the Layout
- Painting ( visible content of the page can be converted to pixels)

Explore Critical render path in Chrome’s performance panel 

Render blocking resources?
- CSS is render blocking but can also be non-render blocking if it's not used
- JS is a parser blocking resource but can be avoided with `async` attr

SSR vs Client vs SSG

use colors to separate chapters

When you hit save -> JSX -> transpiler -> vanilla JS -> includes [document.createElement()]

How the internet works
- Packets: a small segment of a larger message. Each packet contains both data and information about that data
- Protocols:  a protocol is a standardized way of doing certain actions and formatting data so that two or more devices are able to communicate with and understand each other.

So when you take down production just say, hay man, it's complicated