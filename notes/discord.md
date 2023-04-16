Discord is really an engineering marvel. In one of the Y-combinator chats, I found people praising Discord for its great engineering. With just 40 engineers in 2017, they were able to scale to 2.5 million concurrent voice call users. How did they do that?


1. The answer to this is not very simple. Discord is an engineering marvel. First things first, Discord uses WebRTC like other conferencing platforms but with a twist.

2. WebRTC is the technology for real-time audio/video communication. It performs various tasks in this communication:1) Signal processing to remove ambient noise from the audio or video 2) Codec handling to compress and decompress the audio or video. 3) Routing from one peer to another through firewalls, (NATs), and relays to create an Interactive Connectivity Establishment (ICE).

3. But, there are various issues with directly using it. Discord made some changes with it to suit their use case. 1)This involved controlling the system volume which is generally attenuated by windows during a call. Discord didn't want this because they required both game and the user's sound.2) They reduce your bandwidth and CPU utilization during periods of silence.

4. Apart from that, Discord uses client-server networking architecture because peer-to-peer becomes expensive when the number of users is large > 1000. This helps to prevent your computers from DDOS attacks because your public IP is not visible.

5. They reduce the amount of information shared to maintain connections and also remove ICE which is used to determine the best path in the peer-to-peer network. This helps to increase performance.

6. The Backend services for Discord responsible for maintaining connections between clients and sending signals are all written in Elixir which builds on top of Erlang and aids in concurrent processing.

7. They use consistent hashing to determine the server to be assigned to a particular client, but that too with some modifications, because that also has bottlenecks that cause a decrease in performance.
