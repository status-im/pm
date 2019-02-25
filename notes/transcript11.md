0:00 - 1:00

Oskar: Welcome to the eleventh Status Core Dev Call. We have quite a lot of things on the agenda today. We did a poll SMT voting to find the things people want to talk the most about. We'll start from the top and see how far we get with the time we have. Also just a small PSA, if you go to the repository, status-im/pm, we have a index of all the previous videos and notes if you want to refer back. Let's get started, so the first topic is Whisper availability inside Status Dapp browser, which is something that will benefit Teller Network as well as Gas Relayer and possibly others. So I guess Richard, would like to elaborate on it if you don't mind?

1:00 - 2:00

Richard: So basically we are going to do the development of the Gas Relayer and Teller Network. We saw that we have a need to have Whisper available in all the apps, mostly because we want all the apps to be able to communicate between each other. What the rest of the team working on the Gas Relayer and Teller Network and I wanted to know is what is the coordinate state of this functionality and what would it take for Dutch to be able to use Whisper in the (Work Tree?) provider that the Status provides?

Status (Dutch?): Well since I've been discussing this before, probably since it's building, I have improved my answer. So first question is, do you need this functionality only when the Dapp is open in the status browser or do you need it to send the synchronous notifications to somewhere.

Richard: Probably what scenarios would be useful?

2:00 - 3:00

Status (Dutch?): So for the first one it's pretty trivial to just allow the namespace and we already blocked the... by default Whisper has a pretty poor API in terms of security, so if we just allow you all the whisper API you would be able to take the private keys and replace them. So we already limit them so we can allow this while the app is running, basically Javascript is being executed in the browser. That will not help you to do anything synchronous while the app is running. So we were discussing things like for instance, you get a notification that you won the bet, and you need to send the notification, for that it is pretty useless to just allow it in status browser.

3:00 - 4:00

Status (Dutch?): For that we thought about different things, and I even had a hacked version of Status Whisper that allows you to in Javascript make a whisper envelope, and just use a HTTP/RPC API to send it. But then the problem is where to host it. I know that there was a huge pushback against hosting our own server with that because of the distance realization reasons, so that's our biggest issue right now. What will be this place where you go and call this RPC API when there is no status client active. That's where we stopped. Otherwise it's a technically solvable issue.

Iuri: So already having the first case supported that will be a huge help.

4:00 - 5:00

Status (Dutch?): So just inside the browser right?

Iuri: Yeah that would already be a big help.

Status (Dutch?): Yeah so just ping me on Status, I will add it to our backlog, and I will try to just make an update to Status GO and it will allow this namespace, it's pretty trivial.

Ricardo: So just a question about this namespace. It needs to be locked because if you allow anything at Whisper you could also make transactions or anything using that?

Status (Dutch?): Essentially you can pretend to be someone else and replace the keys and things like this, so all this API Whisper doesn't split for some reason, like management API vs. normal user API's so if you allow all whisper API's you will have all Admin API's which you dont want. So what we did is we made a whitelist of methods that we can allow. Right now we just block everything Whisper, but we can allow POST, which is probably the method you want if you want to send stuff.

5:00 - 6:00

Status (Dutch?): And also creating filters and reading from filters which is also a question. Do you need to be allowed to read from Whisper, otherwise you will theoretically be able to read all the messages from all the chats.

Jarrad: Is it possible to blacklist the Whisper public key that the user is logged in as?

Status (Dutch?): Yeah it's also possible, we can do whatever we want we intercept all the calls and inspect them at runtime, right now what we implemented is we whitelisted the POST method or something like that, but we can blacklist as well just in case.

Iuri: We would need the public key for identity purposes.

6:00 - 7:00

Status (Dutch?): But you need a seperate, or do you need the same public key as the user? Because you if you use POST it will use keys as a user. Or this is private keys I'm talking about. The public keys you probably can use whatever you want.
