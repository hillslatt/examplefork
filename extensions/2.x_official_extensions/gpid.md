### Global Placement Id(gpid)

**Sponsor**: The Trade Desk

**Goal**:
The Global Placement ID (GPID) was an initiative in the Fall of 2021 led by the TradeDesk to solve the problem of inventory identification in an industry-wide way. It aims to give buyers a way to identify a given ad slot on a page across SSPs and header bidding integrations. 

**Background**:
It all starts with how publishers decide to label their ad slots: the places on their pages where ads can be served. In some ad servers like GAM, these things are called “ad units”. Most publishers use unique ad slot names, but some publishers utilize the same name for every ad slot on their page. e.g. “/homepage” might be the name for 5 different slots.

It’s the case of ‘same ad slot names’ that Prebid Ad Slot and GPID are meant to address.


### Object: GPID <a name="object_gpid"></a>

While there is no single format for GPID syntax, it is important to keep GPIDs unique to each ad slot on the page, consistent in syntax, and informative, as placements are included in reporting and are used by sophisticated buyers for targeting.

### Using Ad Unit Codes and Div IDs as GPIDs
While there is no single format for GPID syntax, it is important to keep GPIDs unique, consistent in syntax, and informative, as placements are included in reporting and are used by sophisticated buyers for targeting.

For ease of adoption, where applicable, a Google Ad Manager (GAM) or DoubleClick For Publishing (DFP) ad unit code alone can serve as an effective GPID.

* If the ad unit code alone is sufficient to uniquely identify a placement, use it as a GPID
* If the ad unit code alone is not sufficient to uniquely identify a placement, append the Div ID of the placement after its ad unit code to construct a GPID

For details on how publishers typically pass Div IDs to their respective SSPs and exchanges, see the [Prebid documentation](https://docs.prebid.org/features/pbAdSlot.html). 


<strong>General Guidelines</strong>
* Focus on the placement that is being sold.
* Avoid including any information that that's already in another part of the bid request. For example, there is no need to include domain, ad format, seller, if it's a mobile placement, and so on.
* Provide a descriptive, named placement rather than a numerical or alphanumerical one.
* Use delimiters, preferably forward slashes (/).
* Apply consistent formatting.

<strong>IMPORTANT:</strong> If you choose to include additional information in a GPID, make sure that the placement portion can be easily identified and extracted in a consistent manner for all placements transacted.

### Getting to gpid using Ad Unit Code

Some publishers have unique and consistent GPIDs within ad unit codes. In these cases, there is no need to include Div IDs in GPIDs, as ad unit codes suffice. Here are some GPID examples constructed using only ad unit codes.

  <table>
  <tr>
    <td><strong>Ad Unit Code Code&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</strong></td>
    <td><strong>Example gpid</strong></td>
  </tr>
  <tr>
    <td><code>123456/unique-placement-name</td>
    <td>123456/unique-placement-name</td>
  </tr>
</table>

### Using Ad Unit Codes and Div IDs as GPIDs

  <table>
  <tr>
    <td><strong>Ad Unit Code&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</strong></td>
    <td><strong>DIV ID&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</strong></td>
    <td><strong>gpid</strong></td>
  </tr>
  <tr>
    <td><code>123456/example.com/homepage</code></td>
    <td>image_top</td>
    <td>123456/example.com/homepage/image_top</td>
  </tr>
</table>

### Example Request

```

{
  "imp": {
   "ext": {
   "gpid": "123456/example.com/homepage/image_top"
   }
     }
        }