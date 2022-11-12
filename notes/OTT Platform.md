How Does Content From OTT (Over-The-Top) Platforms Reach You?

1. Let's start from the basics. When we browse any website, we are connected via multiple HTTP requests which are sent over a TCP connection maintained 
   between the client and the server. We also know, that for real-time systems like chat applications, we use Web Sockets instead of HTTP connections. 
   Now, the question comes, what type of connection is maintained during streaming and how is the data actually transferred?

2. Answering the first question, the type of connection that is maintained while streaming is called the HTTP streaming connection.

3. The "HTTP streaming" mechanism keeps a request open indefinitely. It never terminates the request or closes the connection, even after 
   the server pushes data to the client. This mechanism significantly reduces the network latency because the client and the server do not 
   need to open and close the connection.

4. The basic life cycle of an application using "HTTP streaming" is as follows:
    1) The client makes an initial request and then waits for a response.
    2) The server defers the response to a poll request until an update is available, or until a particular status or timeout has occurred.
    3) Whenever an update is available, the server sends it back to the client as a part of the response.
    4) The data sent by the server does not terminate the request or the connection. The server returns to step 3.

5. Now we know the connection type used for streaming, as HTTP depends on TCP, the underlying connection is TCP. 
   Now let's discuss how the data actually travels.

6. For this, HTTP live streaming (HLS) protocol is used. An HLS stream originates from a server where (in on-demand streaming) 
   the media file is stored, or where (in live streaming) the stream is created.

7. Two main processes take place on the server:1) Encoding: The video data is reformatted so that any device can recognize and interpret the data. 
   HLS must use H.264 or H.265 encoding.2) Segmenting: The video is divided up into segments a few seconds in length. 
   In addition to dividing the video into segments, HLS creates an index file of the video segments to record the order they belong in.
   HLS will also create several duplicate sets of segments at different quality levels: 480p, 720p, 1080p, and so on.

8. Then these segments are supplied over CDN which then makes these available to the client which is your device- laptop or mobile on which 
   you are streaming contents.

9. One of the advantages HLS has over some other streaming protocols is adaptive bitrate streaming.

10. There are some other streaming protocols too like DASH. A lot of people prefer DASH over HLS.
