As of my last knowledge update in January 2022, I can provide information on the features introduced in Java up to version 17. I don't have specific details on versions beyond that. Here is a summary of major features introduced in Java from version 9 to version 17:

### Java 9
- Anonymous Classes
- HTTP/2 Client
- Private Methods in interface
	(Only default method can assess them)
	Call APIs in java, supports HTTP/1 and HTTP/2, synchronous and asynchronous and web sockets.
	HttpClient client = HttpClient.newHttpClient();


### Java 10 (2018)
- var
- Optional*.orElseThrow ()


### Java 11 (2018)
- Local-Variable Syntax for Lambda Parameters:
	(@Nonnull var s1, @Nullable var s2) -> s1 + s2
- New methods in String


### Java 12 (2019)
- multiple Switch Expressions and ways to use them


### Java 13 (2019)
1.  Text Blocks (""" """)


### Java 14 (2020)
- Records
- more in Switch
- Pattern Matching for instanceOf:


### Java 15 (2020)
- Sealed Classes (Preview)


### Java 16 (2021)
-


### Java 17 (2021)
- Sealed Classes
- Pattern Matching for switch

### Java 18 ,19
- nothing special


### Java 20
- Scoped Values


### Java 21
- Virtual Threads
	Thread virtualThread = Thread.ofVirtual().start(() -> {
		System.out.println("Hello from a virtual thread!");
	});
- Records pattern matching
	obj instanceOf Point (double x, double y)
	(Only for Records)
- STR."{{varable}}" - preview