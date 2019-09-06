# Subcontracting

Adds an object for information on the subcontracted portion of the contract.

## Guidance

If there the percentage of the contract value that is subcontracted is an exact value and not a range, set `minimumPercentage` and `maximumPercentage` to the same number.

## Legal context

In the European Union, this extension's fields correspond to [eForms BG-709 (Second Stage)](https://github.com/eForms/eForms). See [OCDS for the European Union](http://standard.open-contracting.org/profiles/eu/master/en/) for the correspondences to Tenders Electronic Daily (TED).

## Examples

```json
{
"awards": [
          {
            "id": "1",
            "hasSubcontracting": true,
            "subcontracting": {
              "value": {
                "amount": 28000,
                "currency": "EUR"
              },
              "details": "The painting and electricity tasks are subcontracted."
            }
          }
        ]
}
```

```json
{
"awards": [
          {
            "id": "1",
            "hasSubcontracting": true,
            "subcontracting": {
              "minimumPercentage": 0.3,
              "maximumPercentage": 0.3,
              "details": "The painting and electricity tasks are subcontracted."
            }
          }
        ]
}
```

## Issues

Report issues for this extension in the [ocds-extensions repository](https://github.com/open-contracting/ocds-extensions/issues), putting the extension's name in the issue's title.
