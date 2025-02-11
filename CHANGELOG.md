Changelog
=========

2.5.2
-----
  - Remove harmful terminology, following [the Puppetlabs components name changes](https://puppet.com/blog/removing-harmful-terminology-from-our-products/) ([#216](https://github.com/voxpupuli/pypuppetdb/pull/216))
  - Use built-in unittest.mock instead of mock ([#228](https://github.com/voxpupuli/pypuppetdb/pull/228))
  - Build and test dependencies updates. 

Thanks to the following contributors of this release: [@pgajdos](https://github.com/pgajdos).

2.5.1
-----

  - Fix TypeError exception thrown by `BaseAPI._query()` when using debug logging.

Thanks to Ben Roberts for his contribution!

2.5.0
-----

  - Python 3.10 added as a supported version
    ([#213](https://github.com/voxpupuli/pypuppetdb/pull/213))

2.4.0
-----

  - Added PQL support with `pql()` method
    (PR [#201](https://github.com/voxpupuli/pypuppetdb/pull/201),
     fixes [#167](https://github.com/voxpupuli/pypuppetdb/issues/167))
  - Added ability to specify additional queries when using `Node.facts()`
    ([#127](https://github.com/voxpupuli/pypuppetdb/pull/127))
  - Improve the documentation (even more ;))
    (PR [#206](https://github.com/voxpupuli/pypuppetdb/issues/206),
     fixes [#143](https://github.com/voxpupuli/pypuppetdb/issues/143)
     and [#129](https://github.com/voxpupuli/pypuppetdb/issues/129))
  - Fixed creating `Edge` objects
    ([#202](https://github.com/voxpupuli/pypuppetdb/issues/202))
  - Python 3.9 added as a supported version
    ([#203](https://github.com/voxpupuli/pypuppetdb/pull/203))

2.3.0
-----

  - Added support for `with` statement
    ([#185](https://github.com/voxpupuli/pypuppetdb/pull/185))
  - Added explicit `disconnect()` method
    ([#185](https://github.com/voxpupuli/pypuppetdb/pull/185))
  - Improved the documentation on [Read the Docs](https://pypuppetdb.readthedocs.io/en/latest/)
    and in the project's README 
    ([#190](https://github.com/voxpupuli/pypuppetdb/pull/190))

2.2.0
-----

  - Loosen requirements and drop six

2.1.0
-----

  - Bugfix: Fixed <span class="title-ref">metric()</span> function to
    query the new v2 endpoint based on Jolokia
    (<https://jolokia.org/reference/html/protocol.html>)
  - Added a new parameter
    <span class="title-ref">metric\_api\_version</span> to the
    <span class="title-ref">BaseAPI()</span> constructor that allows
    changing the version of the <span class="title-ref">metric</span>
    API being queried. Valid values are
    <span class="title-ref">'v1'</span> for PuppetDB \<= 6.9.0,
    <span class="title-ref">'v2'</span> for PuppetDB \>= 6.9.1 or
    <span class="title-ref">None</span> which defaults to
    <span class="title-ref">'v2'</span>.
  - Added a mew parameter <span class="title-ref">version</span> to the
    <span class="title-ref">metric()</span> function that allows
    overriding the version of the metric API being queried for that
    individual call. If nothing is specified it will default to the
    <span class="title-ref">self.metric\_api\_version</span> of the
    class, else it expects a value of
    <span class="title-ref">'v1'</span> or
    <span class="title-ref">'v2'</span> same as the
    <span class="title-ref">metric\_api\_version</span> class parameter.
  - Added new <span class="title-ref">payload</span> parameter to
    <span class="title-ref">\_query()</span> to allow users to send
    arbitrary payloads with their queries (useful for debugging).

2.0.0
-----

  - Dropping old python 2.7/3.5 and ensuring 3 latest versions are
    supported
  - Adding mypy + cleanup + further removal of python2 code
  - Bugfix: Httpretty is not used outside tests and breaks install on
    newer python versions for some systems

1.2.0
-----

  - Add option to get nodes without using event-counts
  - define the project status as stable
  - bundle requirements-test.txt in python package

1.1.0
-----

  - deduplicate dependencylist
  - QueryBuilder.py: Use native data structures for internal
    representation
  - Add support for the Command API, /pdb/cmd/v1. Added \_cmd alongside
    \_query to minimise changes to original code

1.0.0
-----

  - Bump dependencies
  - QueryBuilder: Added support for FromOperator, arrays and
    FromOperator
  - New endpoint: status
  - POST query in request body
  - Simplify JSON encoding for POST
  - Upload and publish is built in to setuptools

0.3.3
-----

  - Add support for authentication with tokens
  - Fix bug with parsing results from inventory endpoint

0.3.2
-----

  - Fixed noop puppet runs reporting unchanged instead of noop.
  - Fixed unreported nodes shown as 'noop' in puppetdb \> 4.1.0.
  - Add Inventory API endpoint for PuppetDB 4.2.0.
  - Support for producer field on catalogs, facts and report types.

0.3.1
-----

  - Fixed a datetime related bug in
    <span class="title-ref">pypuppetdb.api.nodes()</span> that caused
    all returned nodes to be an unreported status

0.3.0
-----

  - New QueryBuilder module allows users to build PuppetDB queries in an
    Object-Oriented fashion.
  - Adding support for new fields provided in PuppetDB 4.1.0.

0.2.3
-----

  - Removed deprecation of
    <span class="title-ref">pypuppetdb.types.Report.events()</span>.
    Expanded resource events data timestamps are not parseable.
  - Escaping additional path parameters passed to \_url() with
    urllib.quote

0.2.2
-----

  - Fixed URL Encoding found when querying the specific value of a
    macaddress fact.
  - Adding support for PuppetDB 4.0.0 information. Namely Adding a
    catalog\_uuid attribute to the Catalog type object. Adding code\_id,
    catalog\_uuid and cached\_catalog\_status attributes to the Report
    type object.
  - Removing unneeded sudo option from .travis.yml, this gave
    unnecessary warning in the test environment.
  - Updating the files under docs/ so
    <https://pypuppetdb.readthedocs.org/en/latest/> can be updated
  - Deprecating
    <span class="title-ref">pypuppetdb.types.Report.events()</span> in
    favour of the new events list variable.
  - Renaming test-requirements.txt to requirements.txt

0.2.1
-----

  - Adding a version comparison utility function using examples provided
    in
    <http://stackoverflow.com/questions/1714027/version-number-comparison>
  - Adding a new variable latest\_report\_hash to the Node object.
    Default None but is given a real value from the field of the same
    name in the Nodes endpoint available in PuppetDB 3.2 or higher.
  - Allowing support for 'GET' AND 'POST' requests in the api \_query()
    function. This will allow clients to send requests to the PuppetDB
    that are too long for a GEt request query string
  - Adding a node field, code\_id, to the Catalog object using the field
    of the same name from the Catalogs endpoint (currently unused as of
    PuppetDB 3.2.2)
  - Adding test cases for new features EXCEPT the GET and POST update.

0.2.0
-----

  - Version bump to 0.2.0
  - Adding support for v4 of the Query API
  - Removing v2 and v3 api functions as per changelog
  - pypuppetdb will no longer support multiple API versions, removing
    the api\_version attribute from pypuppetdb.connect()
  - All clients must remove the api\_version attribute from the connect
    function, or the starting number, since it is no longer supported
  - Removing all NotImplemented errors in the function of BaseAPI and
    filled them with the real code

**New Features**

New endpoints:

  - `environments`: `environments()`
  - `factsets`: `factsets()`
  - `fact-paths`: `fact_paths()`
  - `fact-contents`: `fact_contents()`
  - `edges`: `edges()`

Changes to Types:

  - `pypupperdb.types.Report` now requires `api` to be passed as the
    second argument, this allows to directly query for any events that
    occurred in this report object. This functionality was proposed and
    denied because of backward compatability reasons, since the previous
    versions are now removed this is no longer a problem.
  - All `pypupperdb.types.*` accept the v4 API information as optional
    parameters. These parameters are primarily environment related but
    may include additional information if provided from that endpoint.
  - Functions appearing inside `pypuppetdb.types` that run queries
    against the PuppetDB now accept and passing additional keyword
    arguments to the query.
  - All `pypuppetdb.BaseAPI` functions pass any received keyword
    arguments to the `pypuppetdb.api.__init__._query()` function. This
    allows for easy integration with paging functions and parameters.

0.1.1
-----

  - Fix the license in our `setup.py`. The license shouldn't be longer
    than 200 characters. We were including the full license tripping up
    tools like bdist\_rpm.

0.1.0
-----

Significant changes have been made in this release. The complete v3 API
is now supported except for query pagination.

Most changes are backwards compatible except for a change in the SSL
configuration. The previous behaviour was buggy and slightly misleading
in the names the options took:

  - `ssl` has been renamed to `ssl_verify` and now defaults to `True`.
  - Automatically use HTTPS if `ssl_key` and `ssl_cert` are provided.

For additional instructions about getting SSL to work see the Quickstart
in the documentation.

**Deprecation**

Support for API v2 will be dropped in the 0.2.x release series.

**New features**

The following features are **only** supported for **API v3**.

The `node()` and `nodes()` function have gained the following options:

  - `with_status=False`
  - `unreported=2`

When `with_status` is set to `True` an additional query will be made
using the `events-count` endpoint scoped to the latest report. This will
result in an additional `events` and `status` keys on the node object.
`status` will be either of `changed`, `unchanged` or `failed` depending
on if `events` contains `successes` or `failures` or none.

By default `unreported` is set to `2`. This is only in effect when
`with_status` is set to `True`. It means that if a node hasn't checked
in for two hours it will get a `status` of `unreported` instead.

New endpoints:

  - `events-count`: `events_count()`
  - `aggregate-event-counts`: `aggregate_event_counts()`
  - `server-time`: `server_time()`
  - `version`: `current_version()`
  - `catalog`: `catalog()`

New types:

  - `pypuppetdb.types.Catalog`
  - `pypuppetdb.types.Edge`

Changes to types:

  - `pypuppetdb.types.Node` now has:
      - `status` defaulting to `None`
      - `events` defaulting to `None`
      - `unreported_time` defaulting to `None`

0.0.4
-----

Due to a fairly serious bug 0.0.3 was pulled from PyPi minutes after
release.

When a bug was fixed to be able to query for all facts we accidentally
introduced a different bug that caused the `facts()` call on a node to
query for all facts because we were resetting the query.

  - Fix a bug where `node.facts()` was causing us to query all facts
    because the query to scope our request was being reset.

0.0.3
-----

With the introduction of PuppetDB 1.5 a new API version, v3, was also
introduced. In that same release the old `/experimental` endpoints were
removed, meaning that as of PuppetDB 1.5 with the v2 API you can no
longer get access to reports or events.

In light of this the support for the experimental endpoints has been
completely removed from pypuppetdb. As of this release you can only get
to reports and/or events through v3 of the API.

This release includes preliminary support for the v3 API. Everything
that could be done with v2 plus the experimental endpoints is now
possible on v3. However, more advanced funtionality has not yet been
implemented. That will be the focus of the next release.

  - Removed dependency on pytz.
  - Fixed the behaviour of `facts()` and `resources()`. We can now
    correctly query for all facts or resources.
  - Fixed an issue with catalog timestampless nodes.
  - Pass along the `timeout` option to `connect()`.
  - Added preliminary PuppetDB API v3 support.
  - Removed support for the experimental endpoints.
  - The `connect()` method defaults to API v3 now.

0.0.2
-----

  - Fix a bug in `setup.py` preventing successful installation.

0.0.1
-----

Initial release. Implements most of the v2 API.
