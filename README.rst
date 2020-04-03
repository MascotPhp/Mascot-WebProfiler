Silex Web Profiler
==================

The Mascot Web Profiler service provider allows you to use the wonderful
Symfony web debug toolbar and the Symfony profiler in your Mascot application.

To install this library, run the command below and you will get the latest
version:

.. code-block:: bash

    composer require 'mascot/web-profiler:^0.1'

And enable it in your application:

.. code-block:: php

    use Mascot\Provider;

    $app->register(new Provider\WebProfilerServiceProvider(), array(
        'profiler.cache_dir' => __DIR__.'/../cache/profiler',
        'profiler.mount_prefix' => '/_profiler', // this is the default
    ));

The provider depends on ``ServiceControllerServiceProvider``,
``TwigServiceProvider``, and ``HttpFragmentServiceProvider`` so you also need
to enable those if that's not already the case:

.. code-block:: php

    $app->register(new Provider\HttpFragmentServiceProvider());
    $app->register(new Provider\ServiceControllerServiceProvider());
    $app->register(new Provider\TwigServiceProvider());

If you are using ``FormServiceProvider``, the ``WebProfilerServiceProvider``
will detect that and enable the corresponding panels.

*Make sure to register all other required or used service providers before*
``WebProfilerServiceProvider``.

If you are using ``MonologServiceProvider`` for logs, you must also add
``symfony/monolog-bridge`` as a Composer dependency to get the
logs in the profiler.

If you are using ``VarDumperServiceProvider``, add ``symfony/debug-bundle`` as
a Composer dependency to display VarDumper dumps in the toolbar and the
profiler.

If you are using ``symfony/security``, add ``symfony/security-bundle`` as
a Composer dependency to display Security related information in the toolbar
and the profiler.
