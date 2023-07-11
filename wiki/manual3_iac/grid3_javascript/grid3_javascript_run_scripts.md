> IMPORTANT NOTICE (05/03/2023): 
The information of this page is outdated. ThreeFold team is in the process of migrating this this manual to its new home on manual.grid.tf. Please go to [manual.grid.tf](https://manual.grid.tf/) to read the latest documentation of ThreeFold.

## How to run the scripts

- Set your grid3 client configuration in `scripts/client_loader.ts` or easily use one of `config.json`
- update your customized deployments specs
- Run using [ts-node](https://www.npmjs.com/ts-node)

```bash
npx ts-node --project tsconfig-node.json scripts/zdb.ts
```

or

```bash
yarn run ts-node --project tsconfig-node.json scripts/zdb.ts
```

