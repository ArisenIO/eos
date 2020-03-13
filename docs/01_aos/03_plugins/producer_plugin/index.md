# producer_plugin

## Description

The `producer_plugin` loads functionality required for a node to produce blocks.

[[info]]
| Additional configuration is required to produce blocks. Please read [Configuring Block Producing Node](https://developers.rsn.io/arisen-aos/docs/environment-producing-node).

## Usage

```console
# config.ini
plugin = arisen::producer_plugin [options]
```
```sh
# aos startup params
aos ... -- plugin arisen::producer_plugin [options]
```

## Options

These can be specified from both the `aos` command-line or the `config.ini` file:

```console
Config Options for arisen::producer_plugin:

  -e [ --enable-stale-production ]      Enable block production, even if the 
                                        chain is stale.
  -x [ --pause-on-startup ]             Start this node in a state where 
                                        production is paused
  --max-transaction-time arg (=30)      Limits the maximum time (in 
                                        milliseconds) that is allowed a pushed 
                                        transaction's code to execute before 
                                        being considered invalid
  --max-irreversible-block-age arg (=-1)
                                        Limits the maximum age (in seconds) of 
                                        the DPOS Irreversible Block for a chain
                                        this node will produce blocks on (use 
                                        negative value to indicate unlimited)
  -p [ --producer-name ] arg            ID of producer controlled by this node 
                                        (e.g. inita; may specify multiple 
                                        times)
  --private-key arg                     (DEPRECATED - Use signature-provider 
                                        instead) Tuple of [public key, WIF 
                                        private key] (may specify multiple 
                                        times)
  --signature-provider arg (=RSN6MRyAjQq8ud7hVNYcfnVPJqcVpscN5So8BhtHuGYqET5GDW5CV=KEY:5KQwrPbwdL6PhXujxW37FSSQZ1JiwsST4cqQzDeyXtP79zkvFD3)
                                        Key=Value pairs in the form 
                                        <public-key>=<provider-spec>
                                        Where:
                                           <public-key>    is a string form of 
                                                           a vaild ARISEN public
                                                           key
                                        
                                           <provider-spec> is a string in the 
                                                           form <provider-type>
                                                           :<data>
                                        
                                           <provider-type> is KEY, or AWALLETD
                                        
                                           KEY:<data>      is a string form of 
                                                           a valid ARISEN 
                                                           private key which 
                                                           maps to the provided
                                                           public key
                                        
                                           AWALLETD:<data>    is the URL where 
                                                           awalletd is available 
                                                           and the approptiate 
                                                           wallet(s) are 
                                                           unlocked
  --awalletd-provider-timeout arg (=5)     Limits the maximum time (in 
                                        milliseconds) that is allowed for 
                                        sending blocks to a awalletd provider for 
                                        signing
  --greylist-account arg                account that can not access to extended
                                        CPU/NET virtual resources
  --produce-time-offset-us arg (=0)     offset of non last block producing time
                                        in microseconds. Negative number 
                                        results in blocks to go out sooner, and
                                        positive number results in blocks to go
                                        out later
  --last-block-time-offset-us arg (=0)  offset of last block producing time in 
                                        microseconds. Negative number results 
                                        in blocks to go out sooner, and 
                                        positive number results in blocks to go
                                        out later
  --max-scheduled-transaction-time-per-block-ms arg (=100)
                                        Maximum wall-clock time, in 
                                        milliseconds, spent retiring scheduled 
                                        transactions in any block before 
                                        returning to normal transaction 
                                        processing.
  --incoming-defer-ratio arg (=1)       ratio between incoming transations and 
                                        deferred transactions when both are 
                                        exhausted
  --producer-threads arg (=2)           Number of worker threads in producer 
                                        thread pool
  --snapshots-dir arg (="snapshots")    the location of the snapshots directory
                                        (absolute path or relative to 
                                        application data dir)
```

## Dependencies

* [`chain_plugin`](../chain_plugin/index.md)

### Load Dependency Examples

```console
# config.ini
plugin = arisen::chain_plugin [operations] [options]
```
```sh
# command-line
aos ... --plugin arisen::chain_plugin [operations] [options]
```