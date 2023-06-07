# Subcontracting

Adds objects for information about the terms governing subcontracting and the parts of the contract that tenderers and suppliers will subcontract to third parties.

## Guidance

If you are using the [Lots extension](https://extensions.open-contracting.org/en/extensions/lots/master/), [follow its guidance](https://extensions.open-contracting.org/en/extensions/lots/master/#usage) on whether to use `tender.lots` fields or `tender` fields.

If the percentage of the contract value that is subcontracted is an exact number and not a range, set `minimumPercentage` and `maximumPercentage` to the same number.

## Legal context

In the European Union, this extension's fields correspond to [article 21 of directive 2009/81/EC](https://eur-lex.europa.eu/legal-content/EN/TXT/HTML/?uri=CELEX:32009L0081&from=EN#d1e2623-76-1) and the following [eForms business terms](https://docs.ted.europa.eu/eforms/latest/reference/business-terms/):

* BT-773 (Subcontracting)
* BT-553 (Subcontracting Value)
* BT-554 (Subcontracting Description)
* BT-555 (Subcontracting Percentage)
* OPT-301 (Main Contractor ID Reference, Subcontractor ID Reference)
* BT-64 (Subcontracting Obligation Minimum)
* BT-65 (Subcontracting Obligation)
* BT-729 (Subcontracting Obligation Maximum)

For correspondences to eForms fields, see [OCDS for eForms](https://standard.open-contracting.org/profiles/eforms/latest/en/). For correspondences to Tenders Electronic Daily (TED), see [OCDS for the European Union](http://standard.open-contracting.org/profiles/eu/master/en/).

## Examples

### Tender and awards

In the following example, information about the terms governing subcontracting is disclosed at the tender and award stages, and information about the parts of the contract that the supplier will subcontract is disclosed at the award stage.

```json
{
  "tender": {
    "subcontractingTerms": {
      "description": "The successful tenderer is obliged to specify which part or parts of the contract it intends to subcontract beyond the required percentage and to indicate the subcontractors already identified."
    }
  },
  "awards": [
    {
      "id": "1",
      "hasSubcontracting": true,
      "subcontracting": {
        "competitive": true,
        "value": {
          "amount": 28000,
          "currency": "EUR"
        },
        "minimumPercentage": 0.3,
        "maximumPercentage": 0.3,
        "competitiveMinimumPercentage": 0.1,
        "competitiveMaximumPercentage": 0.25,
        "description": "The painting and electricity tasks are subcontracted."
      }
    }
  ]
}
```

### Lots and bids

In the following example, information about the terms governing subcontracting is disclosed per lot at the tender stage, and information about the parts of the contract that the tenderer will subcontract is disclosed at the bid stage.

```json
{
  "parties": [
    {
      "id": "ORG-0005",
      "roles": [
        "tenderer"
      ]
    },
    {
      "id": "ORG-0012",
      "roles": [
        "subcontractor"
      ]
    }
  ],
  "tender": {
    "lots": [
      {
        "id": "1",
        "subcontractingTerms": {
          "description": "The contractor must subcontract a minimum percentage of the contract using the procedure set out in Title III of Directive 2009/81/EC.",
          "competitiveMinimumPercentage": 0.255,
          "competitiveMaximumPercentage": 0.455
        }
      }
    ]
  },
  "bids": {
    "details": [
      {
        "id": "1",
        "hasSubcontracting": true,
        "subcontracting": {
          "description": "The subcontracting will be...",
          "value": {
            "amount": 9999999.99,
            "currency": "EUR"
          },
          "minimumPercentage": 0.3,
          "maximumPercentage": 0.3,
          "subcontracts": [
            {
              "id": "1",
              "subcontractor": {
                "id": "ORG-0012",
                "name": "Company ABC"
              },
              "tenderers": [
                {
                  "id": "ORG-0005",
                  "name": "Tendering Company Ltd"
                }
              ]
            }
          ]
        }
      }
    ]
  }
}
```

## Issues

Report issues for this extension in the [ocds-extensions repository](https://github.com/open-contracting/ocds-extensions/issues), putting the extension's name in the issue's title.

## Changelog

### 2023-05-22

* Add fields for eForms:
  * `Bid.hasSubcontracting`
  * `Bid.subcontracting`
  * `SubcontractingTerms.competitiveMaximumPercentage`
  * `SubcontractingTerms.competitiveMinimumPercentage`
  * `Subcontracting.subcontracts`
* Update descriptions for eForms:
  * `Subcontracting`
  * `Subcontracting.description`
  * `Subcontracting.value`
* Add 'subcontractor' to party role codelist.

### 2022-07-18

* Add `Lot.subcontractingTerms` field.

### 2020-10-07

* Rename the `subcontracting` field in the `Tender` object to `subcontractingTerms`.

### 2020-04-24

* Add `minProperties`, `minItems` and/or `minLength` properties.

This extension was originally discussed as part of the [OCDS for EU profile](https://github.com/open-contracting-extensions/european-union/issues) and in [pull requests](https://github.com/open-contracting-extensions/ocds_subcontracting_extension/pulls?q=is%3Apr+is%3Aclosed). You can also see discussions about this extension in [this issue](https://github.com/open-contracting-extensions/ocds_subcontracting_extension/issues/2).
