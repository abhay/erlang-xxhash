erlang-xxhash [![Build Status](https://travis-ci.org/pierresforge/erlang-xxhash.png)](https://travis-ci.org/pierresforge/erlang-xxhash)
=============

Simple Erlang wrapper for the [xxHash](http://code.google.com/p/xxhash/) algorithm.


Usage
-----

```erlang
application:start(xxhash).
Text = "test".
Seed = 12345.


%% Simple usage

xxhash:hash32(Text, Seed).               % => 3834992036
xxhash:hash32(Text).                     % => 1042293711

xxhash:hash64(Text, Seed).               % => 7624679986283906467
xxhash:hash64(Text).                     % => 5754696928334414137


%% Advanced usage

Handle32 = xxhash:hash32_init(Seed).
xxhash:hash32_update(Handle32, Text).      % => ok
xxhash:hash32_digest(Handle32).            % => 3834992036 (Intermediate digest)
xxhash:hash32_update(Handle32, <<"Foo">>). % Support for binary values.
xxhash:hash32_update(Handle32, 42).        % Support for integers.
xxhash:hash32_update(Handle32, 13.37).     % Support for floats.
xxhash:hash32_update(Handle32, moo).       % Support for atoms.
xxhash:hash32_digest(Handle32).            % => 3243777239

Handle64 = xxhash:hash64_init(Seed).
xxhash:hash64_update(Handle64, Text).      % => ok
xxhash:hash64_digest(Handle64).            % => 7624679986283906467 (Intermediate digest)
xxhash:hash64_update(Handle64, <<"Foo">>). % Support for binary values.
xxhash:hash64_update(Handle64, 42).        % Support for integers.
xxhash:hash64_update(Handle64, 13.37).     % Support for floats.
xxhash:hash64_update(Handle64, moo).       % Support for atoms.
xxhash:hash64_digest(Handle64).            % => 10617254975351441063
```


Licenses
--------

This program is distributed under the MIT License.

xxHash library is distributed under New BSD License.


Author
------

Pierre Matri <pierre@matri.me>
