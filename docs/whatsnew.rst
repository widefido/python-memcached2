What's New in python-memcachee2
*******************************

Wed May 8, 2013

  * MemcacheValue is now called ValueSuperStr, and it is no longer the
    default return type in Memcache().  It can be defined by passing
    ValueMemcache to Memcache() as the "value_wrapper".  There's also
    a ValueDictionary now.
  * Adding ValueDictionary class.
  * Memcache() class no longer returns MemcacheValue class.
    It returns a normal string, unless you have specified a value_wrapper
    attribute during the creation of the Memcache object.

Tue May 7, 2013

  * Adding MANIFEST.in file.
  * Adding CASFailure to MemcacheValue methods.

Fri May 3, 2013

  * I did a short performance test against the python-memcached
    library that this is meant to replace.  This new module is around 10%
    faster (using the Memcache() class) at retrieving 10 byte values, and
    16% faster at 1KB values.  I was expecting more, but I also haven't
    done any performance tuning.  If I just return normal strings instead
    of ValueSuperStr, that goes up to 23% faster, so that may be a point
    of optimization.
  * Adding remaining methods to MemcacheValue.

Thu May 2, 2013

  * MemcacheValue now has "set()" method.

Wed May 1, 2013

  * I'm tagging a 0.2 but still not going to release to pypi
    yet.  Server failure testing, related to ExceptionsAreMissesMapping,
    have located several exceptions that weren't being caught and
    translated into local module exceptions.  Current functionality is
    solid, but I want to add a MemcacheCASValue class, which is kind of
    an API change.
  * Improving Python 2 BrokenPipeError
  * Catching more exceptions, more tests.

    Added more extensive testing to ExceptionsAsMissesMapping, including
    in the cases where the server disconnects.  Through that, found places
    where more exceptions needed to be caught.

Tue Apr 30, 2013

  * Trapping ServerDisconnected exception.

Mon Apr 29, 2013

  * ObliviousMapping renamed ExceptionsAreMissesMapping

    ExceptionsAreMissesMapping suggested by Wes Winham.  Thanks!

Sat Apr 27, 2013

  * The module is usable, but if you do you
    should expect that the interfaces may change.  The high level
    :py:class:`~memcached2.ExceptionsAreMissesMapping code is usable but
    not fully tested and the exceptions aren't all caught.  The low-level
    :py:class:`~memcached2.Memcache` code is basically complete, documented,
    and well tested.
  * Bringing back KeyError because d.get() is preferable.
  * Renaming ObliviousDict to ObliviousMapping.

Fri Apr 26, 2013

  * Adding ObliviousDict() tests and fixing "in".