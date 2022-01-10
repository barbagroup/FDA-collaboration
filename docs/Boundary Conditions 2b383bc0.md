## OpenFoam BC for the incompressible flow:

for the first case we set up BC for the velocity as at inlet:

&#x20;    `type            fixedValue;
    value           uniform (0 0 0.521646);`

for walls

`type            noSlip;`

and at outlet we set up advective BC:

```
  type            advective;
  value           phi;
```

<br>
