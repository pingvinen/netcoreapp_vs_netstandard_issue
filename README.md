So I ran into this issue...
===========================

I had a need to remove [diacritics](https://en.wikipedia.org/wiki/Diacritic) from strings, and have previously used [`String.Normalize`](https://msdn.microsoft.com/en-us/library/system.string.normalize(v=vs.110).aspx) for that.

Trying to re-use this code in a dotnet core project however turned out to be problematic.

I was trying to put the code into a library project (i.e. target framework `netstandard1.6`). To my surprise the code failed to compile. The compiler insists that `String.Normalize` does not exist.

I found this to be very odd, as I had found [articles describing diacritics removal in dotnet core](https://adamhathcock.blog/2017/05/04/generating-url-slugs-in-net-core/) using this exact method.

It turns out that if I change the target framework to `netcoreapp1.1` then the compiler is happy - why?


Getting an answer
-----------------

I created [issue 393](https://github.com/dotnet/standard/issues/393) with the `dotnet/standard` people :)
