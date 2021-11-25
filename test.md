# ActiveCampaign Abandoned Cart Module

Contents:

* [Summary](#summary)
    * [Issue](#issue)
    * [Decision](#decision)
    * [Status](#status)
* [Details](#details)
    * [Assumptions](#assumptions)
    * [Constraints](#constraints)
    * [Positions](#positions)
    * [Argument](#argument)
    * [Implications](#implications)
* [Related](#related)
    * [Related decisions](#related-decisions)
    * [Related requirements](#related-requirements)
    * [Related artifacts](#related-artifacts)
    * [Related principles](#related-principles)
* [Notes](#notes)


## Summary


### Issue

We want to sync Magento abandoned cart into ActiveCampaign.
* We want to develop an automatic interface for sync Magento abandoned cart into ActiveCampaign.
* We want to also provide a manual interface to solve the automatic syncing issue.

### Decision


This specific abandoned cart module decides the Magento abandoned cart's syncing into the ActiveCampaign.
* This abandoned cart module provides automatic syncing using CRON.
* This abandoned cart module also provides a manual syncing way using the Magento admin panel.


### Status

Decided. We are open to new alternatives as they arise.


## Details


### Assumptions

This custom module can be disabled without affecting Core module connection.

Complete Abandoned Cart syncing related code is on this dedicated module and code is easy to understand for whoever the developer maintaining.


### Constraints

Whether this Abandoned Cart module requires maintenance, the rest of dependant modules will not be affected, but syncing of abandoned carts may be affected or stopped.



### Positions

For synchronization methods, we considered these solutions:

* Magento Plugins design pattern

* Magento Observers design patterns

For batch synchronization methods, we considered these solutions:

* Batch sync with cron tasks

* Batch sync with Magento command development.

* Manual Batch sync from admin.

Is it required a custom admin grid for abandoned carts or the native report from Magento is good enough? 



### Argument

Summary per solution:

* Magento Plugins design pattern: rejected because of no need of modify behavior of Magento Core functionallity.

* Magento Observers design patterns: ideal solution due to observers can be easily implemented and treat errors and exceptions without affecting Magento flow.

* Batch sync with Magento command development: rejected due to intervention need from a developer.

* Batch sync with cron tasks: better solution for an automatic syncing process.

* Manual Batch sync from admin: this solution has been taken as accepted because offers easy access to process syncing of carts manually.

* Custom admin grid will be developed due to a better listing of abandoned carts required for ActiveCampaign; some important data is required for collecting this information: email, totals and items in cart, and most important, an abandoned cart is considered since the moment of their creation. 


### Implications

Magento's knowledge is important for developing and maintaining this module.

Magento topics to consider to learn:

* Magento Observers design pattern
* Magento cron tasks implementation
* Customize Magento admin panel
* Magento database structure modification
* Creation of Magento admin grid


## Related


### Related decisions

The use of Guzzle HTTP for consuming API (Core module) must be completed and fully understood.
Also is important to complete to develop of dependent modules: Order and Customer.


### Related requirements



### Related artifacts



### Related principles

Code quality over deadlines.


## Notes
