
.. _libdoc_compile_mode:

======================================
:mod:`mode` -- controlling compilation
======================================

.. module:: aesara.compile.mode
   :platform: Unix, Windows
   :synopsis: controlling compilation
.. moduleauthor:: LISA

Guide
=====

The ``mode`` parameter to :func:`aesara.function` controls how the
inputs-to-outputs graph is transformed into a callable object.

Aesara defines the following modes by name:

- ``'FAST_COMPILE'``: Apply just a few graph optimizations and only use Python implementations.
- ``'FAST_RUN'``: Apply all optimizations, and use C implementations where possible.
- ``'DebugMode'``: A mode for debugging. See :ref:`DebugMode <debugmode>` for details.
- ``'NanGuardMode``: :ref:`Nan detector <nanguardmode>`
- ``'DEBUG_MODE'``: Deprecated. Use the string DebugMode.

The default mode is typically ``FAST_RUN``, but it can be controlled via the
configuration variable :attr:`config.mode`, which can be
overridden by passing the keyword argument to :func:`aesara.function`.

.. TODO::

    For a finer level of control over which optimizations are applied, and whether
    C or Python implementations are used, read.... what exactly?


Reference
=========

.. attribute:: FAST_COMPILE

.. attribute:: FAST_RUN

.. class:: Mode(object)

    Compilation is controlled by two attributes: the `optimizer` controls how
    an expression graph will be transformed; the `linker` controls how the
    optimized expression graph will be evaluated.

    .. attribute:: optimizer

        An :class:`optimizer` instance.

    .. attribute:: linker

        A :class:`linker` instance.

    .. method:: including(*tags)

        Return a new Mode instance like this one, but with an
        optimizer modified by including the given tags.

    .. method:: excluding(*tags)

        Return a new Mode instance like this one, but with an
        optimizer modified by excluding the given tags.

    .. method:: requiring(*tags)

        Return a new Mode instance like this one, but with an
        optimizer modified by requiring the given tags.
