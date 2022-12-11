Hotstar served 25 million concurrent users with the live stream of India vs Pakistan World Cup match. Before Hotstar, the record was held by youtube with 
8 million concurrent users. These days Jio Cinema is streaming FIFA Worldup and it is extremely glitchy and now we realise how amazing Hotstar does its job with 
live streaming.

But, before Hotstar, we use to watch matches on our television. What changed? How is that different from the Hotstar stream?

1. First of all, live does not mean a millisecond difference. Before live streaming applications, live TV already existed which was used for streaming news, 
   and cricket/football matches. The delay in those broadcasts could be anywhere between 5-20 seconds. This difference has been used a lot by bookies in cricket 
   matches to make money.

2. Now, let’s understand, why this delay exists in a live TV broadcast. Television signals can be broadcast through a transmitter, that sends audio and video signals 
   to people’s homes through cables/satellites(with dish antennas).

3. A video is a collection of pictures that change at a rate and seem to create a moving effect.This is a raw video. A raw video has a big size, and has to be 
   compressed to be broadcasted. During a live stream, the video from the camera is first encoded. It is a way to compress the video into sizeable chunks without 
   compromising quality.

4. Once, a video is encoded it is sent by a transmitter through satellite or tv towers to your homes.

5. Then came, live streaming. This is what Hotstar does. The process of encoding remains the same. But now, the video has to pass through the streaming website and 
   reach you through the internet(optical fiber cables laid under the sea).

6. In Live streaming, the servers receive the encoded video, but they have to then transmit it to the viewers. To make this happen, there needs to be an open 
   connection between the users and the servers. This connection generally relies on a persistent TCP connection which is maintained between the client and server. 
   This can be done with the help of a Websocket. The protocols used for this are generally HLS or MPEG-DASH. 

7. But, these servers can be anywhere in the world, the connection creation time and data transfer time can be huge and cause a huge delay.

8. That’s where CDNs come into the picture, the live video(chunks) are cached in CDN and the content to the users is served through this CDN. Hotstar uses Akamai as 
   its CDN. The stream goes from the server to the CDN where it is cached and then reaches you through the CDN.

6. So, all this is happening, there must be some lag in this also. Before HLS and MPEG DASH this lag used to be as high as a minute. But, with these protocols, 
   the lag has been reduced to 3-10 seconds. But, sometimes, TV broadcasts will still be faster than live streaming. 
