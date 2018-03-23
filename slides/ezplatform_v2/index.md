## &nbsp;

<center><img class="scale70" title="ezsystems" src="img/whats_new_in_ezplatformv2.png"/></center>

---

<center><img class="scale70" title="ezsystems" src="img/who_we_are.png"/></center>

--

## History

<center><img title="ezsystems" src="img/ezpublish_ezplatform.png"/></center>

- eZ Publish 3,4(Legacy)   
- eZ Publish 5 (Legacy,Symfony)  
- eZ Platform 1,**2** (Symfony)

---

# eZ Platform V2

--

## Improvements

- Symfony 3.4 (LTS)
- Support of new bundles on core components
- Increase eZ development speed
- Increase partners and customers development speed
- Improve speed of the U.I for editors
- Reduce learning curve for developers

--

## Be Symfony3 and 4 ready

```
services:
    _defaults:
        autowire: true
        autoconfigure: true
        public: false
    _instanceof:
            App\AppBundle\Handler\AppInterface:
                tags: ['my.app']

    App\AppBundle\Services\MyService:
        #Scalar arguments must be autowired manually
        $argument: !tagged my.app

    App\:
        resource: '../../src/AppBundle/*'
        exclude: '../../src/AppBundle/{Entity,Migrations,Tests}'
```

--

## Admin UI

- Pure Symfony 3.4 and Bootstrap 4
- Using KnpMenuBundle for menus
- Symfony Forms for editing
- React for rich components:
  - Universal Discovery Widget (UDW)
  - RichText (Alloy Editor)
  - Subitems
  - LandingPage editor ( to follow 2.2)

--

## Admin UI

- Siteaccess for admin
  - Template & Controllers customisation
  - Content View overrides
  - Theming with eZ Platform Design Engine

---

# eZ Platform Cloud

--

## On-premise/IAAS way

- AWS
- Azure
- Google Cloud Platform
- Open stack
- IBM Cloud Computing, Linode, Digital ocean
- Doc help: <a  href ="https://doc.ezplatform.com/en/1.11/guide/clustering/" >Clustering</a> , <a href ="https://doc.ezplatform.com/en/1.11/cookbook/setting_up_amazon_aws_s3_clustering/" >AWS S3</a>

--

## On-premise/IAAS way

<center><img class="scale50" src="img/clustering.png" title"ezplatform clustering" /></center>

--

## Platform architecture complexity

<center> LAMP <br /> to <br /> [LNMpPf7VHMS](https://www.netgenlabs.com/Blog/Dealing-with-the-complexity-of-eZ-Platform-architecture)</center>

--

<div style="text-align:left;"><small>
**Debian**

<p>- Jessie(8) , Security updates until(May 2018),LTS (May 2020)</p>
<p>- Stretch(9) , Security updates until(TBA), LTS (June 2022)</p>

</small></div>

<div style="text-align:left;"><small>
**Ubuntu**
<p>- Xenial(16.04.4) RD (March 2018), EOL (April 2021) </p>
</small></div>

<div style="text-align:left;"><small>
**CentOS**
<p>- (7), Release date (July 2014), Full update(Q4 2020), Maintenance updates(June 2024)</p>
<small>Each CentOS version is maintained for up to 10 years (According to the Red Hat Enterprise Linux (RHEL), CentOS team (2012)</small>
</small></div>

<div style="text-align:left;"><small>
**PHP**
<p>- (7.2) Supported until (November 2020)</p>
</small></div>

...

--

## Theory of evolution

<center><img src="img/phone_comp.png" title"phone_comp"/></center>

--


## eZ Platform Cloud (PAAS)

<center><img class="scale70" src="img/paas_abs.png" title"ezplatform cloud" /></center>

--

## eZ Platform Cloud (PAAS)

<center><img class="scale60" title="platform.sh" src="img/platform_sh.png"/></center>

--

## eZ Platform Cloud (PAAS)

<center><img class="scale70" src="img/platformsh_region.png" title"ezplatform cloud" /></center>

--

#### eZ Platform Cloud (PAAS)

<center><img class="scale50" src="img/platform_sh_infrastructure.png" title"ezplatform cloud" /></center>

--

## eZ Platform Cloud

- Supported on eZ Platform 1.13LTS, 2.x and higher
- With Platform.sh config out of the box
- Faslty bundle available for Enterprise subscribers

--

## DEMO

---

# eZ Commerce

--

## Combining technologies and approaches

<center><img class="scale70" src="img/ezcommerce/combining_technologie_01.png" title"ezplatform commerce" /></center>

--

## Combining technologies and approaches

<center><img class="scale70" src="img/ezcommerce/combining_technologie_02.png" title"ezplatform commerce" /></center>

--

## Combining technologies and approaches

<center><img class="scale70" src="img/ezcommerce/combining_technologie_03.png" title"ezplatform commerce" /></center>

--

## How about a Content + Commerce Platform

<center><img class="scale70" src="img/ezcommerce/combining_technologie_04.png" title"ezplatform commerce" /></center>

--

## Introducing eZ Commerce (BETA)

<center><img class="scale70" src="img/ezcommerce/ezcommerce_beta.png" title"ezplatform commerce" /></center>

--

## Product Structure

<center><img class="scale70" src="img/ezcommerce/ezcommerce_plugin.png" title"ezplatform commerce" /></center>

--

## eZ Commerce

- E-shop for B2B and B2C
- Blending content and commerce , Easily manage your product catalog and editorial content
- Connectors to `SAP, MS Dynamics, Salesforce, Zuora, SugarCRM, Netsuite, Paypal ...`

**eZ Commerce will also be available to run on eZ Platform Cloud**

--

## DEMO

---

# Features 2.0

--

## Link Manager

<center><img title="ezsystems" src="img/link_manager.png"/></center>

--

## Extending UI

<center><img title="ezsystems" src="img/extending_ui.png"/></center>

- Symfony EventListner
- KnpMenuBundle

https://github.com/ezsystems/ezplatform-ui-2.0-introduction

--

## Content Reverse Relations

<center><img title="ezsystems" src="img/reverse_relations.png"/></center>

--

## Translation Manager

<center><img title="ezsystems" src="img/translation_manager.png"/></center>

--

## URL Management

<center><img title="ezsystems" src="img/url_alias_manager.png"/></center>

--

##  Features 2.1

--


## Custom Tags

```
system:
    default:
        fieldtypes:
            ezrichtext:
                custom_tags: [ezyoutube]

ezrichtext:
    custom_tags:
        ezyoutube:
            template: 'EzSystemsExtendingTutorialBundle:field_type/ezrichtext/custom_tag:ezyoutube.html.twig'
            icon: '/bundles/ezplatformadminui/img/ez-icons.svg#video'
            attributes:
                title:
                    type: 'string'
                    required: true
                    default_value: ''
                video_url:
                    type: 'string'
                    required: true
                width:
                    type: 'number'
                    required: true
                    default_value: 640
```

--

## Object states

- Object states enable you to create sets of custom states and then assign them to Content.
- They can be used in conjunction with permissions.

<center><img title="ezsystems" src="img/object_state_lock.png"/></center>

--

## Content on the fly

- Content on the fly enables you to create new Content anywhere in the application from the Universal Discovery widget

<center><img title="ezsystems" src="img/cotf.png"/></center>

--

## URL alias management

- You can now add custom URL aliases to Content items from the URL tab.
- Aliases can be set per language of the Content item.

<center><img title="ezsystems" src="img/url_aliases_manger2.png"/></center>

--

## REST

**GET Location that matches URL alias**

- When user provides parameter in URL, Location with given URL Alias is returned via `GET /content/locations`.

**search with FieldCriterion**

- You can now perform REST search via `POST /views` using custom `FieldCriterion`. This allows you to build custom content logic queries with nested logical operators OR/AND/NOT.

--

## Simplified filtered search

- During search you can now filter the results by Content type, Section, Modified and Created dates.

<center><img title="ezsystems" src="img/filtered_search.png"/></center>

--

## Other UI improvements

- When accessing the Back Office from a link to a specific Content item, after logging in you will now be redirected to the proper content view.

- In edit mode you can now preview content as it will look in any SiteAccess it is available in.

--


- When you start editing a Content item that already has an open draft, you will see a draft conflict screen

<center><img title="ezsystems" src="img/draft_conflict.png"/></center>


--

- Forgot password

<center><img title="ezsystems" src="img/forgot_password.png"/></center>

--

- Change password

<center><img title="ezsystems" src="img/change_password.png"/></center>

--

## Doc Improvement

**Creating a UDW tab**

- The Universal Discovery Widget (UDW) is a separate React module.

<center><img title="ezsystems" src="img/images_tab_in_udw.png"/></center>

--

Others:

**REST API guide audit**

**FieldType Tutorial**

**Extending tutorial v2**

**...**

---

# Release Cycle & Roadmap 2018

--

## eZ Platform 2018 Release Cycle

<center><img title="ezsystems" src="img/release_cycle.png"/></center>

--

## Roadmap 2018

<center><img title="ezsystems" src="img/roadmap.png"/></center>

---

### Thank you

|                   |                                                                             |
|-------------------|:----------------------------------------------------------------------------|
| We                |**http://ez.no**                                                             |
| Installation      |**https://ezplatform.com<br> https://github.com/ezsystems**                  |
| Documentation     |**http://doc.ezplatform.com (NEW)<br> https://doc.ez.no**                    |
| Contact us        |**https://ezcommunity.slack.com<br> https://discuss.ezplatform.com (NEW)**   |
