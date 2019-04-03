---
title: Virtual MGA API Docs

language_tabs: # must be one of https://git.io/vQNgJ
  - shell: cURL
  - php: PHP

toc_footers:
  - <a href='http://www.virtualmga.com'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/lord/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction

<a href='www.virtualmga.com'>Virtual MGA</a> helps underwriters and organizations more effectively build and distribute their insurance products online to their trading partners.  VMGA offers an in-house underwriting platform to not only manage their rating, underwriting rules, and document generation;
but also to manage their capacity by tracking aggregates across a variety of exposure and premium attributes.  
<ul><li>Our <a href="#brit-homeguard-api">Brit HomeGuard API</a> can supply coverholders with a quote from a set of risk details for a location or fully manage the entire policy lifecyle of the risk with functions that include create, bind, endorse, and renewal.</li></ul>

<aside class="success">
Please send an e-mail to <a href="mailto:webservices@virtualmga.com">webservices@virtualmga.com</a> for any issues or inquiries to our API online.
</aside>

# Authentication

```shell
curl -X POST \
  https://brit.virtualmga.com/restservice/ \
  -H 'Authorization: Basic YnJpdGFwaUB2aXJ0dWFsbWdhLmNvbTpCcml0YXBpdGVzdDE=' \
  -H 'Content-Type: application/xml' \

 ```
 
 ```php
 <?php

$request = new HttpRequest();
$request->setUrl('https://brit.virtualmga.com/restservice/');
$request->setMethod(HTTP_METH_POST);

$request->setHeaders(array(
  'Authorization' => 'Basic YnJpdGFwaUB2aXJ0dWFsbWdhLmNvbTpCcml0YXBpdGVzdDE=',
  'Content-Type' => 'text/xml'
));

```

 
Virtual MGA provides a REST API over HTTPS.  Unencrypted HTTP is not supported due to data privacy requirements.  Authentication will be handled using basic HTTPS authentication. 

The communication mechanism to encapsulate data is XML.  The only supported HTTP method is POST.  Any attached XML samples are the only supported POST data sets.  All request headers should contain a content-type of application/xml. 

A username and password is required to allow access to the API. You can register a new coverholder by sending an e-mail to <a href="mailto:webservices@virtualmga.com">webservices@virtualmga.com</a> with your specific request.

Virtual MGA expects you to pass your credentials as a Base64-encoded header or as parameters in an HTTP client.  When you pass your credentials in the header, you must Base64-encode them.  The following is an example of an encoded
HTTP Basic Authentication header:


`Authorization: Basic YnJpdGFwaUB2aXJ0dWFsbWdhLmNvbTpCcml0YXBpdGVzdDE`



# Brit HomeGuard API

## Create Submission


```shell
curl -X POST \
  https://brit.virtualmga.com/restservice/ \
  -H 'Authorization: Basic YnJpdGFwaUB2aXJ0dWFsbWdhLmNvbTpCcml0YXBpdGVzdDE=' \
  -H 'Content-Type: application/xml' \
  -d '<template>
  <template_id>brit_homeguard_create_submission</template_id>
  <request>
    <underwriter_id>10000</underwriter_id>
    <effective_date>2019-03-15</effective_date>
    <expiration_date>2020-03-15</expiration_date>
    <entity_type>Individual</entity_type>
    <applicant>
      <first_name>Gus</first_name>
      <middle_name>New</middle_name>
      <last_name>Test</last_name>
      <full_name></full_name>
      <dba></dba>
      <co_applicant_full_name></co_applicant_full_name>
      <address>
        <location_street_number>8110</location_street_number>
        <location_street_address>Ranch Road 2222</location_street_address>
        <location_unit_number>Apt 53</location_unit_number>
        <location_zip>78730</location_zip>
        <location_city>Austin</location_city>
        <location_state>TX</location_state>
        <location_county>Travis</location_county>
      </address>
      <mailing_address>
        <mailing_street_number>8110</mailing_street_number>
        <mailing_street_address>Ranch Road 2222</mailing_street_address>
        <mailing_unit_number>Apt 53</mailing_unit_number>
        <mailing_zip>78730</mailing_zip>
        <mailing_city>Austin</mailing_city>
        <mailing_state>TX</mailing_state>
      </mailing_address>
    </applicant>
  </request>
</template>
'
```

```php
<?php

$request = new HttpRequest();
$request->setUrl('https://brit.virtualmga.com/restservice/');
$request->setMethod(HTTP_METH_POST);

$request->setHeaders(array(
  'Authorization' => 'Basic YnJpdGFwaUB2aXJ0dWFsbWdhLmNvbTpCcml0YXBpdGVzdDE=',
  'Content-Type' => 'application/xml'
));

$request->setBody('<template>
  <template_id>brit_homeguard_create_submission</template_id>
  <request>
    <underwriter_id>10000</underwriter_id>
    <effective_date>2019-03-15</effective_date>
    <expiration_date>2020-03-15</expiration_date>
    <entity_type>Individual</entity_type>
    <applicant>
      <first_name>Gus</first_name>
      <middle_name>New</middle_name>
      <last_name>Test</last_name>
      <full_name></full_name>
      <dba></dba>
      <co_applicant_full_name></co_applicant_full_name>
      <address>
        <location_street_number>8110</location_street_number>
        <location_street_address>Ranch Road 2222</location_street_address>
        <location_unit_number>Apt 53</location_unit_number>
        <location_zip>78730</location_zip>
        <location_city>Austin</location_city>
        <location_state>TX</location_state>
        <location_county>Travis</location_county>
      </address>
      <mailing_address>
        <mailing_street_number>8110</mailing_street_number>
        <mailing_street_address>Ranch Road 2222</mailing_street_address>
        <mailing_unit_number>Apt 53</mailing_unit_number>
        <mailing_zip>78730</mailing_zip>
        <mailing_city>Austin</mailing_city>
        <mailing_state>TX</mailing_state>
      </mailing_address>
    </applicant>
  </request>
</template>
');

try {
  $response = $request->send();

  echo $response->getBody();
} catch (HttpException $ex) {
  echo $ex;
}

```


> The above command returns XML structured like this:

```xml
<response>
    <status>Success</status>
    <message>
        <![CDATA[Submission  found. Submission id is '612']]>
    </message>
    <message>
        <![CDATA[App Flow Brit.API.HomeGuard.CreateSubmission executed]]>
    </message>
    <message>
        <![CDATA[Submission  processed.]]>
    </message>
    <request_id>EE0E340D46A511E9A2F874867AF229DE</request_id>
    <submission>
        <success>true</success>
        <response_date>2019-03-14 17:10:12</response_date>
        <app_number>APP-001323</app_number>
    </submission>
</response> 
```

This method creates a new submission on Virtual MGA Platform and returns a unique ID to be used for quote.

### HTTP Request

`POST https://brit.virtualmga.com/restservice/`

### URL Parameters

Field | Required | Value Type | Description | Accepted Values | Validation Rules/Notes
----- | -------- | ----------- | ---------- | --------------- | ----------------------
template | Y | Root element | Main Detail Structure
template_id | Y | String | The API method being invoked | brit_homeguard_create_submission
request | Y | Child of "template" element | Structure underneath template that contains create submission details
underwriter_id | Y | String | Unique Branch ID for coverholder on VMGA
effective_date | Y | Date | The proposed effective date of the policy |  | Cannot backdate more than 60 days from current system date.  Must be in the format of yyyy-mm-dd
expiration_date | Y | Date | The proposed expiration date of the policy |  | Must be at least one day after the effective date.  Must be in the format of yyyy-mm-dd
entity_type | Y | String | Type of corporate entity type of the insured.   | Individual, Partnership, Joint Venture, Corporation, Limited Liability Company, Trust, Other | 
applicant | Y | Child of "request" element | Structure underneath request that contains applicant details |  | 
first_name | Y* | String | First name of the individual applicant. |  | If entity type is NOT individual, use “full_name” instead.
middle_name | N | String | Middle name of  the individual applicant. |  | If entity type is NOT individual, use “full_name” instead
last_name | Y* | String | Last name of the individual applicant. |  | If entity type is NOT individual, use “full_name” instead
full_name | N* | String | Full name of the applicant not an individual |  | Required if entity type is anything other than “Individual”.
dba | N | String | Doing Business As  |  | 
co_applicant_full_name | N | String | Co Applicant Full Name |  | 
address | Y | Child of "request" element | Structure underneath request that contains the address details for the risk |  | 
location_street_number | Y | String | Street number of the primary risk location |  | US address only
location_street_address | Y | String | Street address of the primary risk location |  | US address only
location_unit_number | N | String | Apartment/Suite number of the primary risk location |  | US address only
location_zip | Y | String | Postal code of the primary risk location |  | US zip code only.  5-digit zip code i.e. 90210
location_city | Y | String | City of the primary risk location |  | US city only
location_state | Y | String | State of the primary risk location |  | US state only including DC.  Two-Letter US state abbreviation i.e. AZ.
location_county | Y | String | County of the primary risk location |  | US county only
mailing_address | Y | Child of "request" element | Structure underneath request that contains the mailing address details |  | 
mailing_country | Y | String | County name of the mailing location | United States, Canada | United States or Canada only
mailing_street_number | Y | String | Street number of the mailing location |  | US or CA address only
mailing_street_address | Y | String | Street address of the mailing location |  | US or CA address only
mailing_unit_number | N | String | Apartment/Suite number of the mailing location |  | US or CA address only
mailing_zip | Y | String | Postal code of the mailing location |  | US zip code or CA postal code only.  5-digit zip code i.e. 90210.  CA Postal Code format i.e. A1A 1A1
mailing_city | Y | String | City of the mailing location |  | US city only
mailing_state | Y | String | US State or Canadian Province of the mailing location |  | Two-Letter Abbreviation


<aside class="success">
The response should return "success" in the status node when a successful request is submitted.  The app_number should now be used for requesting a quote.
</aside>

## Rate Submission

```shell
curl -X POST \
  https://britcnfg.virtualmga.com/restservice/ \
  -H 'Authorization: Basic YnJpdGFwaUB2aXJ0dWFsbWdhLmNvbTpCcml0YXBpdGVzdDE=' \
  -H 'Content-Type: text/xml' \
  -H 'Postman-Token: 0ecd31e5-3f9f-484f-a6b9-4c3eaa8397b6' \
  -H 'cache-control: no-cache' \
  -d '<template>
  <template_id>brit_homeguard_rate</template_id>
 
  <request>
		<effective_date>2019-03-04</effective_date>
		<expiration_date>2020-03-04</expiration_date>
		<form_type>HO3</form_type>
		<locations>
			<location>
			<location_number>1</location_number>
			<location_street_number>1</location_street_number>
			<location_street_address>Pasadena Avenue</location_street_address>
			<location_unit_number />
			<location_zip>91030</location_zip>
			<location_city>South Pasadena</location_city>
			<location_state>CA</location_state>
			<location_county>Los Angeles</location_county>
			<high_risk_area_ind>N</high_risk_area_ind>
			<number_families_primary_dwelling>1</number_families_primary_dwelling>
			<wind_coverage_ind>Y</wind_coverage_ind>
			<earthquake_coverage_ind>Y</earthquake_coverage_ind>
			<tuck_under_parking_ind>N</tuck_under_parking_ind>
			<tilt_up_construction_ind>N</tilt_up_construction_ind>
			<retrofitted_to_code_ind>N</retrofitted_to_code_ind>
			<retrofit_year></retrofit_year>
			<california_quake_requirement>LIMITED</california_quake_requirement>
			<masonry_veneer_coverage_ind>Y</masonry_veneer_coverage_ind>
			<distance_to_water>17.63</distance_to_water>
			<construction_type>BV</construction_type>
			<square_feet>2000</square_feet>
			<year_built>1999</year_built>
			<year_renovated>2015</year_renovated>
			<wiring_update_year>2015</wiring_update_year>
			<wiring_update_type>COMPLETE</wiring_update_type>
			<plumbing_update_year>2015</plumbing_update_year>
			<plumbing_update_type>Complete</plumbing_update_type>
			<heating_update_year>2015</heating_update_year>
			<heating_update_type>Complete</heating_update_type>
			<roof_update_year>2015</roof_update_year>
			<roof_update_type>Complete</roof_update_type>
			<roof_shape>GBL</roof_shape>
			<roof_material>CPSHG</roof_material>
			<sprinklers>LOCAL</sprinklers>
			<smoke_alarm>LOCAL</smoke_alarm>
			<burglar_alarm>LOCAL</burglar_alarm>
			<automatic_water_shutoff>NONE</automatic_water_shutoff>
			<hurricane_protection_ind>N</hurricane_protection_ind>
			<dwelling_value>333444</dwelling_value>
			<other_structures>50000</other_structures>
			<personal_property>166722</personal_property>
			<loss_of_use>66689</loss_of_use>
			<liability_limit>EXCLUDED</liability_limit>
			<medical_payments>EXCLUDED</medical_payments>
			<full_limits_trampoline_firearms_ind>N</full_limits_trampoline_firearms_ind>
			<sinkhole_coverage_ind>N</sinkhole_coverage_ind>
			<located_in_brush_zone_ind>Y</located_in_brush_zone_ind>
			<brush_clearance>1000</brush_clearance>
			<wind_deductible_type>WND</wind_deductible_type>
			<set_aop_deductible_as_wind_ind>Y</set_aop_deductible_as_wind_ind>
			<wind_deductible_percent>0</wind_deductible_percent>
			<earthquake_deductible_percent>10</earthquake_deductible_percent>
			<earthquake_deductible_amount xsi:nil="true" />
			<workers_comp_ind>N</workers_comp_ind>
			<number_workers>2</number_workers>
			<aop_deductible_amount>10000</aop_deductible_amount>
			<aop_deductible_percent xsi:nil="true" />
			<occupancy>
				<occupancy_type>P</occupancy_type>
				<dwelling_rental_term_type>NONE</dwelling_rental_term_type>
				<dwelling_rental_term_period></dwelling_rental_term_period>
				<dwelling_under_renovation_ind>N</dwelling_under_renovation_ind>
			</occupancy>
			<ppc>
				<protection_class>1</protection_class>
				<dwelling_within_1000_ft_water_ind>N</dwelling_within_1000_ft_water_ind>
				<responding_fire_dept_in_range_ind xsi:nil="true" />
				<property_accessible_by_road_ind>Y</property_accessible_by_road_ind>
				<property_occupied_daily_ind>Y</property_occupied_daily_ind>
				<property_visible_ind>Y</property_visible_ind>
			</ppc>
			<extended_liability>
				<extend_liability_additional_locations_ind>N</extend_liability_additional_locations_ind>
				<number_additional_locations xsi:nil="true" />
			</extended_liability>
			<optional_coverages>
				<broad_theft_limit xsi:nil="true" />
				<on_and_off_premises_ind>N</on_and_off_premises_ind>
				<earthquake_sprinkler_leakage_ind>N</earthquake_sprinkler_leakage_ind>
				<enhanced_additional_coverages_ind>N</enhanced_additional_coverages_ind>
				<extended_replacement_cost_percent xsi:nil="true" />
				<golf_cart_physical_damage_ind>N</golf_cart_physical_damage_ind>
				<golf_cart_limit xsi:nil="true" />
				<special_form_additions_alterations_ind>N</special_form_additions_alterations_ind>
				<special_form_personal_property_ind>N</special_form_personal_property_ind>
				<recreational_motor_vehicle_liability_ind>N</recreational_motor_vehicle_liability_ind>
				<increased_business_limit xsi:nil="true" />
				<increased_special_liability_limit_ind>N</increased_special_liability_limit_ind>
				<large_loss_deductible_waiver_ind>N</large_loss_deductible_waiver_ind>
				<limited_mold_property_limit xsi:nil="true" />
				<limited_mold_liability_limit xsi:nil="true" />
				<limited_pollution_property_limit xsi:nil="true" />
				<limited_pollution_liability_limit xsi:nil="true" />
				<loss_assessment_limit>1000</loss_assessment_limit>
				<mandatory_evacuation_ind>N</mandatory_evacuation_ind>
				<ordinance_and_law_percent>10</ordinance_and_law_percent>
				<personal_injury_ind>N</personal_injury_ind>
				<personal_property_other_location_percent xsi:nil="true" />
				<excess_personal_property_amount xsi:nil="true" />
				<replacement_cost_certain_structures_ind>Y</replacement_cost_certain_structures_ind>
				<special_computer_coverage_ind>N</special_computer_coverage_ind>
				<tenant_relocation_expenses_ind>N</tenant_relocation_expenses_ind>
				<coc_soft_costs xsi:nil="true" />
				<coc_theft_of_materials xsi:nil="true" />
				<coc_transit xsi:nil="true" />
				<water_backup_limit xsi:nil="true" />
			</optional_coverages>
			<personal_articles_floater>
				<personal_articles>N</personal_articles>
				<deductible_excluded_ind>Y</deductible_excluded_ind>
				<deductible_amount xsi:nil="true" />
				<blanket_fine_arts_breakage_limit xsi:nil="true" />
				<blanket_fine_arts_non_breakage_limit xsi:nil="true" />
				<blanket_jewelry_limit xsi:nil="true" />
				<cameras_limit xsi:nil="true" />
				<fine_arts_breakage_scheduled_limit xsi:nil="true" />
				<fine_arts_non_breakage_scheduled_limit xsi:nil="true" />
				<furs_limit xsi:nil="true" />
				<golf_equipment_limit xsi:nil="true" />
				<firearms_limit xsi:nil="true" />
				<mens_jewelry_limit xsi:nil="true" />
				<musical_instruments_limit xsi:nil="true" />
				<stamps_limit xsi:nil="true" />
				<coins_limit xsi:nil="true" />
				<silverware_limit xsi:nil="true" />
				<womens_jewelry_limit xsi:nil="true" />
				<vault_jewelry_limit xsi:nil="true" />
				<wine_collections_limit xsi:nil="true" />
				<blanket_wine_collections_limit xsi:nil="true" />
			</personal_articles_floater>
		</location>
		</locations>
	</request>
</template>'
```


> The above command returns XML structured like this:

```xml
  <response>
    <status>Success</status>
    <message>
        <![CDATA[Request processing..]]>
    </message>
    <message>
        <![CDATA[App Flow Brit.API.HomeGuard.Rate executed]]>
    </message>
    <request_id>D482B2CB49A111E9A2F874867AF229DE</request_id>
    <rate>
        <success>true</success>
        <response_date>2019-03-18 12:18:29</response_date>
        <rater_version_applied>v2.220</rater_version_applied>
        <packages>
            <package>
                <name>Standard</name>
                <premium>5895</premium>
                <locations>
                    <location>
                        <location_number>1</location_number>
                        <location_premium>5895</location_premium>
                        <optional_coverages>
                            <ordinance_and_law_percent>10</ordinance_and_law_percent>
                            <replacement_cost_certain_structures_ind>Included</replacement_cost_certain_structures_ind>
                            <inflation_guard_percent>3</inflation_guard_percent>
                            <id_fraud_recovery_limit>25000</id_fraud_recovery_limit>
                            <mechanical_breakdown_limit>100000</mechanical_breakdown_limit>
                            <service_line_limit>10000</service_line_limit>
                            <eco_coverage_limit>50000</eco_coverage_limit>
                        </optional_coverages>
                    </location>
                </locations>
            </package>
        </packages>
    </rate>
</response>
```

This method provides a rating quote for a specific location and set of modifiers.

### HTTP Request

`POST https://brit.virtualmga.com/restservice/`

### URL Parameters

Field | Required | Value Type | Description | Accepted Values | Validation Rules/Notes
----- | -------- | ----------- | ---------- | --------------- | ----------------------
template_id | Y | String | The API method being invoked | brit_homeguard_rate | 
request | Y |  | Structure underneath template that contains the rating details |  | 
effective_date | Y | Date | The proposed effective date of the policy |  | Cannot backdate more than 60 days from current system date.  Must be in the format of yyyy-mm-dd
expiration_date | Y | Date | The proposed expiration date of the policy |  | Must be at least one day after the effective date.  Must be in the format of yyyy-mm-dd
form_type | Y | String | The primary policy coverage type | HO3, HO5, HO6, DP3, HO3_WIND_ONLY, HO6_WIND_ONLY | 
locations | Y |  | Structure underneath request that contains the locations to be rated |  | 
location | Y |  | Repeating structure underneath location that details out each individual location with the rating details for that location |  | 
location_number | Y | Integer | The number of the location |  | Must be greater than 0.
location_street_number | Y | String | Street number of the primary risk location |  | US address only
location_street_address | Y | String | Street address of the primary risk location |  | US address only
location_unit_number | N | String | Apartment/Suite number of the primary risk location |  | US address only
location_zip | Y | String | Postal code of the primary risk location |  | US zip code only.  5-digit zip code i.e. 90210
location_city | Y | String | City of the primary risk location |  | US city only
location_state | Y | String | State of the primary risk location |  | US state only including DC.  Two letter US state abbreviation i.e. CA
location_county | Y | String | County of the primary risk location |  | US county only
high_risk_area_ind | N* | Character | Flag indicating if the location is in a high-risk area as defined by Brit | Y, N | Required if zip/county/state combination for the location is one of any attached in Appendix A
number_families_primary_dwelling | Y | Integer | The number of families in the primary dwelling (not including other structures) |  | Must be greater than or equal to 0.
wind_coverage_ind | Y | Character | Flag to include wind coverage at the location | Y, N | Must be Y if form_type is “HO3_WIND_ONLY” or “HO6_WIND_ONLY”
earthquake_coverage_ind | Y | Character | Flag to include earthquake coverage at the location | Y, N | Must be N if form_type is “HO3_WIND_ONLY” or “HO6_WIND_ONLY”
tuck_under_parking_ind | N* | Character | Flag indicating whether there is tuck under parking at the location | Y, N | Required if earthquake_coverage_ind is “Y”
tilt_up_construction_ind | N* | Character | Flag indicating whether there is tilt up construction at the location | Y, N | Required if earthquake_coverage_ind is “Y”
retrofitted_to_code_ind | N* | Character | Flag indicating if the location has been retrofitted to code | Y, N | Required if earthquake_coverage_ind is “Y”
retrofit_year | N* | Integer | The year the location was retrofitted to code |  | Required if retrofitted_to_code_ind is “Y”.  Must be greater than or equal to year_built.
california_quake_requirement | N* | String | Amount of coverage applied to location in the event of an earthquake loss | FULL, LIMITED | Required if location_state is “CA”.  If earthquake coverage is excluded then this must be “Limited”
masonry_veneer_coverage_ind | N* | Character | Flag indicating if masonry veneer coverage is required at this location | Y, N | Required if earthquake_coverage_ind is “Y”.
distance_to_water | Y | Decimal | Distance to the nearest water source |  | Distance in miles
construction_type | Y | String | The construction type of the location | F, ST, BV, EIFS_BLOCK, M, EIFS, L, SUP, FR | F- Frame, ST – Stucco, BV – Brick Veneer, EIFS_BLOCK – EIFS (Over Block), M – Masonry, EIFS – EIFS (Over Frame), L – Log, SUP - Superior, FR – Fire Resistive
square_feet | Y | Integer | The total square footage for the location |  | Value must be greater than 0.
year_built | Y | Integer | The year the location was built |  | Earliest year built of 1600.  Cannot be more than one year in the future
year_renovated | N | Integer | The year the location was renovated to studs |  | Must be greater than or equal to year_built and cannot be more than one year in the future
wiring_update_year | N | Integer | The year wiring was updated in the location |  | Must be greater than or equal to year_built and cannot be more than one year in the future.  If year_renovated is provided then must be greater than or equal to year_renovated and cannot be more than one year in the future
wiring_update_type | N* | String | Indicates whether there was a partial or complete update | PARTIAL, COMPLETE | Required if wiring_update_year is provided
plumbing_update_year | N | Integer | The year plumbing was updated in the location |  | Must be greater than or equal to year_built and cannot be more than one year in the future.  If year_renovated is provided then must be greater than or equal to year_renovated and cannot be more than one year in the future
plumbing_update_type | N* | String | Indicates whether there was a partial or complete update | PARTIAL, COMPLETE | Required if plumbing_update_year is provided
heating_update_year | N | Integer | The year heating was updated in the location |  | Must be greater than or equal to year_built and cannot be more than one year in the future.  If year_renovated is provided then must be greater than or equal to year_renovated and cannot be more than one year in the future
heating_update_type | N* | String | Indicates whether there was a partial or complete update | PARTIAL, COMPLETE | Required if heating_update_year is provided
roof_update_year | N | Integer | The year the roof was updated on the location |  | Must be greater than or equal to year_built and cannot be more than one year in the future.  If year_renovated is provided then must be greater than or equal to year_renovated and cannot be more than one year in the future
roof_update_type | N* | String | Indicates whether there was a partial or complete update | PARTIAL, COMPLETE | Required if roof_update_year is provided
roof_material | Y | String | The roof material on the location | CPSHG, RUB, TL, CN, MET, WDSHA, SLATE, UNK | CPSHG – Composite Shingle, RUB – Rubber, TL – Tile, CN – Concrete, MET – Metal, WDSHA – Wood Shake, SLATE – Slate, UNK - Unknown
roof_shape | Y | String | The shape of the roof at the location | HIP, FLT_CN, GBL, FLT, BU, OTH, UNK | HIP – Hip, FLT_CN – Flat Concrete, GBL – Gable, FLT – Flat, BU – Built Up, OTH – Other, UNK - Unknown
automatic_water_shutoff | N* | String | Flag indicating if an automatic water shutoff system is present | NONE, LEAK_ALERT, LEAK_SYSTEM, OTHER | If form_type is not “HO3_WIND_ONLY” and “HO6_WIND_ONLY” then this field is required.  LEAK_ALERT – Leak Defense Alert, , LEAK_SYSTEM – Leak Defense System
sprinklers | N* | String | Type of sprinklers that cover at least 90% of the location | NONE, LOCAL, CENTRAL | If form_type is not “HO3_WIND_ONLY” and “HO6_WIND_ONLY” then this field is required.
smoke_alarm | N* | String | Type of smoke alarm present | NONE, CENTRAL, LOCAL, DIRECT | If form_type is not “HO3_WIND_ONLY” and “HO6_WIND_ONLY” then this field is required.
burglar_alarm | N* | String | Type of burglar alarm present | NONE, CENTRAL, LOCAL, DIRECT | If form_type is not “HO3_WIND_ONLY” and “HO6_WIND_ONLY” then this field is required.
hurricane_protection_ind | N* | Character | Flag indicating if a location has approved opening protection | Y, N | Mandatory if location_state = “FL”.  Value is defaulted to “N” if not provided.
dwelling_value | Y | Integer | Value of the location |  | Must be greater than or equal to 0
other_structures | Y | Integer | Value of other structures at the location |  | Must be greater than or equal to 0.  Must be 0 if form_type is “HO6” or “HO6_WIND_ONLY”
personal_property | Y | Integer | Value of personal property at the location |  | Must be greater than or equal to 0
loss_of_use | Y | Integer | Value of additional living expenses |  | Must be greater than or equal to 0
liability_limit | Y | String | Value of liability limit | EXCLUDED, 300000, 500000, 1000000 | If occupancy_type is “COC” then liability must be “Excluded”
medical_payments | Y | String | Value of medical payments limit | EXCLUDED, 2500, 5000, 10000, 25000 | If liability_limit is “Excluded” then this field must also be “Excluded”
full_limits_trampoline_firearms_ind | N* | Character | Flag indicating if full limits should be applied to trampoline liability and firearm liability | Y, N | If liability_limit is not “Excluded” then this field is mandatory.
sinkhole_coverage_ind | N* | Character | Flag indicating if sinkhole coverage is selected for the location  | Y, N | If location state is one of AL,FL,TN,MO,KY then this field is mandatory, otherwise this field should be empty.  This coverage is not available if form_type is “HO3_WIND_ONLY” or “HO6_WIND_ONLY”
located_in_brush_zone_ind | N* | Character | Flag indicating if the property is in a brush zone | Y, N | Mandatory if location_state is one of “CA”, “OR”, “WA”, “ID”, “NV”, “UT”, “AZ”, “WY”, “CO”, “NM”.  If location state is not one of the above, this field should be empty.
brush_clearance | N* | Integer | The distance in feet from the property to the nearest brush |  | Required if located_in_brush_zone_ind is “Y”
wind_deductible_type | N* | String | Denotes what type of coverage the wind deductible is applicable for | WND, NMWND, HRCN | WND – Wind/Hail, NMWND – Named Storm, HRCN – Hurricane, , Mandatory if wind_coverage_ind is “Y”.
set_aop_deductible_as_wind_ind | N* | Character | Indicates if the AOP deductible should be used as the wind deductible | Y, N | Mandatory if wind_coverage_ind is “Y”.  Value must be “N”  if form_type = “HO3_WIND_ONLY” or “HO6_WIND_ONLY”
wind_deductible_percent | N* | Decimal | The deductible to be paid in the event of a wind loss | 1, 2, 3, 5, 10 | 1 – 1%, 2 – 2%, 3 – 3%, 5 – 5%, 10 – 10%.  Mandatory if wind_coverage_ind is “Y” and set_aop_deductible_as_wind_ind is “N”.  If set_aop_deductible_as_wind_ind is “Y” the value in wind_deductible_percent will be ignored.
earthquake_deductible_percent | N* | Decimal | The deductible to be paid in the event of an earthquake loss | 2, 5, 10, 15, 20 | Mandatory if earthquake_coverage_ind is “Y”.  2 – 2%, 5 – 5%, 10 – 10%, 15 – 15%, 20 – 20%.  Only one of earthquake_deductible_percent and earthquake_deductible_amount can be provided.
earthquake_deductible_amount | N* | Integer | The deductible to be paid in the event of an earthquake loss | 25000 | Mandatory if earthquake_coverage_ind is “Y”.  Not available if location_state is one of “CA”,”OR”,”WA”,”UT”,”MT”,”WY”,”SC”,”AR”,”IL”,”IN”,”KY”,”MO”,”MS”,”TN”,”AK”,”HI”.  Only one of earthquake_deductible_percent and earthquake_deductible_amount can be provided.
workers_comp_ind | N* | Character | Flag indicating if worker’s compensation coverage is applied to the location | Y, N | Required if location_state is one of “CA”, “NY”, “NJ”, “NH”.  If location state is not one of the above, this field should be empty.
number_workers | N* | Integer | The number of workers being covered |  | Required if workers_comp_ind is “Y”.  Must be greater than or equal to 0.
aop_deductible_amount | Y | Integer | The deductible to be paid in the event of a loss | 1000, 2500, 5000, 7500, 10000, 15000, 25000, 50000, 75000, 100000, 250000 | If form_type is “HO3_WIND_ONLY” or “HO6_WIND_ONLY” this field should be empty.||Cannot provide an aop deductible amount and an aop deductible percent for the same location.
aop_deductible_percent | Y | Decimal | The deductible to be paid in the event of a loss | 0.5, 1, 2, 3, 5 | Only available if location_state is “TX”.  0.5 – 0.5%, 1 – 1%, 2 – 2%, 3 – 3%, 5 – 5%.  Cannot provide an aop deductible amount and an aop deductible percent for the same location.
occupancy | Y |  | Structure under location that details all the occupancy information for the location |  | 
occupancy_type | Y | String | Dwelling occupancy of the risk | P, SEC, SEASL, RENT, V, COC, MH, CARE | P – Primary|SEC – Secondary, SEASL – Seasonal, RENT – Full Time Rental, V – Vacant, COC – COC/Renovation, MH – Model Home, CARE – Live in Caretaker Only
dwelling_rental_term_type | Y | String | The expected rental period for the primary dwelling structure | NONE, DAYS, WEEKS | 
dwelling_rental_term_period | N* | Integer | The number of days or weeks the primary dwelling structure is rented |  | Required if dwelling_rental_term_type is “Days” or “Weeks”.  Must be greater than or equal to 0.
dwelling_under_renovation_ind | N* | Character | Flag indicating if the location is currently under renovation | Y, N | Required if occupancy_type is “COC”.
ppc | Y |  | Structure under location that details the protection class of the location |  | 
protection_class | N* | String | ISO protection class for the location | 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 10W, SPLIT X, SPLIT Y | If form_type is “HO3_WIND_ONLY” or “HO6_WIND_ONLY” then this field is defaulted to empty. If form_type is not “HO3_WIND_ONLY” or “HO6_WIND_ONLY” then this field is required.
dwelling_within_1000_ft_water_ind | N* | Character | Flag indicating that the location is within 1000 feet of an adequate water source  | Y, N | Required if protection class is one of “9”, ”10”, “10W”, “Split X”, or “Split Y”.  Note:  For protection classes of “10W”, “Split X”, or “Split Y” this water source must be a fire hydrant.
responding_fire_dept_in_range_ind | N* | Character | Flag indicating that the location has a fire department within given distance | Y, N | Required if protection class is one of “9”, ”10”, “10W”, “Split X”, or “Split Y”.  Note:  For a protection class of “9” or “10” this is within 10 minutes or 7.5 miles.  Note:  For a protection class of “10W” this is within 7 miles.  Note:  For protection classes “Split X” and “Split Y” this is within 5 miles.
property_accessible_by_road_ind | N* | Character | Flag indicating that the location is accessible by road year-round | Y, N | Required if protection class is one of “9”, ”10”, “10W”, “Split X”, or “Split Y”.  
property_occupied_daily_ind | N* | Character | Flag indicating that the location is occupied or checked on daily | Y, N | Required if protection class is one of “9”, ”10”, “10W”, “Split X”, or “Split Y”.  
property_visible_ind | N* | Character | Flag indicating that the location is visible to neighbors | Y, N | Required if protection class is one of “9”, ”10”, “10W”, “Split X”, or “Split Y”.  
losses | Y |  | Structure underneath location containing loss information |  | 
loss | N* | Required if losses have occurred at the location | Repeating structure underneath losses for each loss on the location |  |   
loss_date | N* | Date | Date of loss at the location |  | Required if losses have occurred at the location.  Must be in the format of yyyy-mm-dd
loss_amount | N* | Integer | Total loss amount for loss occurring on loss_date |  | Required if losses have occurred at the location.  Must be greater than or equal to 0.
loss_type | N* | String | Description of what caused the loss | EARTHQUAKE, FIRE, FLOOD, LIABILITY, MOLD, OTHER, PERSONAL ARTICLES FLOATER, THEFT, WATER, WIND/HAIL | Required if losses have occurred at the location.
extended_liability | Y |  | Structure underneath location containing the additional location information for extended liability |  | 
extend_liability_additional_locations_ind | N* | Character | Indicates whether liability is going to be extended to other locations | Y, N | If liability_limit is not “EXCLUDED” then this field is mandatory.
number_additional_locations | N* | Integer | The full address of the additional location |  | Required if extend_liability_additional_locations_ind is “Y”.  Must be greater than or equal to 0.
optional_coverages | N |  | Structure underneath location that outlines the optional coverages for the location |  | 
broad_theft_limit | N* | Integer | Limit covered in the event of a loss of personal assets | 2500, 5000, 10000, 25000, 50000, 100000 | Only available for “DP3” form types.  Only available if occupancy_type is one of “P”, “SEC”, “SEASL”, “RENT”, “CARE”.
on_and_off_premises_ind | N* | Character | Indicates whether loss of personal assets can be on or off premises | Y, N | Required if broad_theft_limit is provided.
earthquake_sprinkler_leakage_ind | N | Character | Indicates whether coverage in the event of sprinkler damage due to earthquake is included | Y, N | Only available if form_type is one of “HO3”, “HO5”, “HO6”.  Only available if location_state is one of “CA”, “OR”, “WA”, “SC”, “MO”, “AR”, “KY”, “IL”, “IN”, “UT”, “HI”.  Only available if earthquake_coverage_ind is “Y”.
enhanced_additional_coverages_ind | N | Character |  | Y, N | Not available for form_type of “DP3”.  Not available for “COC” occupancy type.
extended_replacement_cost_percent | N | Decimal | Percentage over the policy limit covered in the event of a loss | 25, 50, 100 | Only available if form_type is one of “HO3”, “HO5”, “HO3_WIND_ONLY”.  Not available for “COC” occupancy type.
golf_cart_physical_damage_ind | N | Character | Indicates if damage to golf carts is covered | Y, N | Only available if occupancy_type is one of “P”, “SEC”, “SEASL”, “RENT”, “CARE”.
golf_cart_limit | N* | Integer | Sum of all golf cart values |  | Required if golf_cart_physical_damage_ind is “Y”.  Must be greater than or equal to 0.
special_form_additions_alterations_ind | N | Character |  | Y, N | Only available if form_type is “HO6”.
special_form_personal_property_ind | N | Character |  | Y, N | Only available if form_type is “HO6”.
recreational_motor_vehicle_liability_ind | N | Character | Indicates if liability on recreational vehicles such as ATVs are covered | Y, N | Not available if liability_limit is “Excluded”.  Not available if form_type is “HO3_WIND_ONLY” or “HO6_WIND_ONLY”.  Not available if occupancy type is one of “MH”, “V”, “COC”.
increased_business_limit | N | Integer | Additional limit added to the existing business limit on the location | 10000, 15000, 25000 | Not available if form_type is “DP3”.  Not available if occupancy type is one of “MH”, “V”, “COC”.
increased_special_liability_limit_ind | N | Character | Indicates if personal or premises liability should have increased limits over what was selected | Y, N | Not available if liability_limit is “Excluded”.  Not available if form_type is “DP3”.  Not available if occupancy type is one of “MH”, “V”, “COC”.
large_loss_deductible_waiver_ind | N | Character | Indicates if the deductible is not applicable in the event of a large loss | Y, N | Only available if form_type is one of “HO3”, “HO5”, “HO6”.  Not available if occupancy_type is “COC”.
limited_mold_property_limit | N | Integer | Amount covered in the event of mold damage to the property | 10000, 25000, 50000, 100000, 250000, 500000, 1000000 | 
limited_mold_liability_limit | N | Integer |  | 10000, 25000, 50000, 100000, 300000 | Not available if liability_limit is “Excluded”.
limited_pollution_property_limit | N | Integer |  | 10000, 25000, 50000, 100000 | Only available if form_type is one of “HO3”, “HO5”, “HO6”.
limited_pollution_liability_limit | N | Integer |  | 10000, 25000, 50000, 100000 | Not available if liability_limit is “Excluded”.  Only available if form_type is one of “HO3”, “HO5”, “HO6”.
loss_assessment_limit | N | Integer | Amount covered in the event of a loss in a shared area | 1000, 2500, 5000, 10000, 25000, 50000, 100000 | 
mandatory_evacuation_ind | N | Character | Indicates if the insured is covered if they are forced to evacuate during a disaster | Y, N | Not available if form_type is “DP3”.  Not available if occupancy_type is one of “MH”, “V”, “COC”.
ordinance_and_law_percent | N | Decimal | Percentage of insured value that is covered if a loss is caused by enforcement of ordinances or laws | 10, 15, 25 | 10 – 10%|15 – 15%|25 – 25%  If occupancy_type is “COC” then only “10” is available.
personal_injury_ind | N | Character | Indicates if personal injury is covered at the location | Y, N | Not available if liability_limit is “Excluded”.  Not available if form_type is “HO3_WIND_ONLY” or “HO6_WIND_ONLY”.  Not available if occupancy_type is “COC”.
personal_property_other_location_percent | N | Decimal |  | 10, 15 | 10 – 10%|15 – Amount Excess of 10%  Not available if occupancy_type is “COC”.
excess_personal_property_amount | N* | Integer | The dollar amount in excess of 10% of insured premises personal property limit |  | Required if personal_property_other_location_percent is “15”.
replacement_cost_certain_structures_ind | N | Character | Flag indicating replacement cost valuation is applied | Y, N | Only available if form_type is one of “HO3”, “HO5”, “HO3_WIND_ONLY”.  Not available if occupancy_type is “COC”.
special_computer_coverage_ind | N | Character | Indicates if computers are covered from non-catastrophic events | Y, N | Not applicable if special_form_personal_property is “Y”.  Only available if form_type is one of “HO3”, “HO5”, “HO6”.  Not available if occupancy_type is one of “MH”, “V”, “COC”.
tenant_relocation_expenses_ind | N | Character | Indicates if coverage is provided if a tenant is forced to move due to a loss | Y, N | Only applicable if location_state is “MA”.  Only applicable if occupancy_type is “RENT” or “CARE”.
coc_soft_costs | N | Integer | Value covered from construction soft costs for COC occupied locations |  | Only available if occupancy_type is “COC”.  Not available if form_type is “DP3”.  Must be greater than or equal to 0.
coc_theft_of_materials | N | Integer | Value covered if construction materials are stolen for COC occupied locations |  | Only available if occupancy_type is “COC”.  Not available if form_type is “DP3”.   Must be greater than or equal to 0.
coc_transit | N | Integer |  |  | Only available if occupancy_type is “COC”.  Not available if form_type is “DP3”.   Must be greater than or equal to 0.
water_backup_limit | N | Integer | Amount covered in the event of water damage from the ground up | 10000, 25000, 50000, 100000, 250000, 500000, 1000000 | 
personal_articles_floater | N |  | Structure under optional_coverages that details out each of the personal articles on the location |  | 
personal_articles | N | Character | Flag indicating if personal articles are being covered for the location. | Y, N | 
deductible_excluded_ind | N* | Character | Flag indicating if the personal articles deductible is excluded for this location | Y, N | Required if personal_articles is “Y”.
deductible_amount | N* | Integer | Amount to be paid in the event of a loss | 2500, 5000, 10000, 15000, 25000, 50000 | Required if personal_articles is “Y”.
blanket_fine_arts_breakage_limit | N | Integer | The total value of all blanketed fine arts with breakage at the location |  | Must be greater than or equal to 0.
blanket_fine_arts_non_breakage_limit | N | Integer | The total value of all blanketed fine arts without breakage at the location |  | Must be greater than or equal to 0.
blanket_jewelry_limit | N | Integer | The total value of all blanketed jewelry at the location |  | Must be greater than or equal to 0.
cameras_limit | N | Integer | The total value of all cameras at the location |  | Must be greater than or equal to 0.
fine_arts_breakage_scheduled_limit | N | Integer | The total value of all scheduled fine arts with breakage at the location |  | Must be greater than or equal to 0.
fine_arts_non_breakage_scheduled_limit | N | Integer | The total value of all scheduled fine arts without breakage at the location |  | Must be greater than or equal to 0.
furs_limit | N | Integer | The total value of all furs at the location |  | Must be greater than or equal to 0.
golf_equipment_limit | N | Integer | The total value of all golf equipment at the location |  | Must be greater than or equal to 0.
firearms_limit | N | Integer | The total value of all firearms at the location |  | Must be greater than or equal to 0.
mens_jewelry_limit | N | Integer | The total value of all men’s jewelry at the location |  | Must be greater than or equal to 0.
musical_instruments_limit | N | Integer | The total value of all musical instruments at the location |  | Must be greater than or equal to 0.
stamps_limit | N | Integer | The total value of all postage stamps at the location |  | Must be greater than or equal to 0.
coins_limit | N | Integer | The total value of all coins at the location |  | Must be greater than or equal to 0.
silverware_limit | N | Integer | The total value of all silverware at the location |  | Must be greater than or equal to 0.
womens_jewelry_limit | N | Integer | The total value of all women’s jewelry at the location |  | Must be greater than or equal to 0.
vault_jewelry_limit | N | Integer | The total value of all jewelry in vaults at the location |  | Must be greater than or equal to 0.
wine_collections_limit | N | Integer | The total value of all wine collections at the location |  | Must be greater than or equal to 0.
blanket_wine_collections_limit | N | Integer | The total value of all blanket wine collections at the location |  | Must be greater than or equal to 0.

## Bind Submission


```

```shell
curl 
```



```



```json

```

This endpoint binds the submission on the VMGA Platform.

### HTTP Request

`POST https://brit.virtualmga.com/restservice/<ID>`

### URL Parameters

Field | Required | Value Type | Description | Accepted Values | Validation Rules/Notes
----- | -------- | ----------- | ---------- | --------------- | ----------------------


