## kalign.wasm

### Usage

```html
<script src="https://cdn.biowasm.com/v2/aioli/latest/aioli.js"></script>
<script type="module">
let CLI = await new Aioli("kalign/3.3.1");

// Create sample data (source: https://github.com/TimoLassmann/kalign/blob/master/dev/data/BB11001.tfa)
await CLI.fs.writeFile("input.fa", `>1aab_
GKGDPKKPRGKMSSYAFFVQTSREEHKKKHPDASVNFSEFSKKCSERWKT
MSAKEKGKFEDMAKADKARYEREMKTYIPPKGE
>1j46_A
MQDRVKRPMNAFIVWSRDQRRKMALENPRMRNSEISKQLGYQWKMLTEAE
KWPFFQEAQKLQAMHREKYPNYKYRPRRKAKMLPK
>1k99_A
MKKLKKHPDFPKKPLTPYFRFFMEKRAKYAKLHPEMSNLDLTKILSKKYK
ELPEKKKMKYIQDFQREKQEFERNLARFREDHPDLIQNAKK
>2lef_A
MHIKKPLNAFMLYMKEMRANVVAESTLKESAAINQILGRRWHALSREEQA
KYYELARKERQLHMQLYPGWSARDNYGKKKKRKREK`);

// Run kalign
let output = await CLI.exec(`kalign input.fa -f fasta -o result.fasta`);
document.write(`<pre>${await CLI.cat("result.fasta")}</pre>`);
console.warn(output);
</script>
```

### Patch
* The `--as-needed` flag causes compilation errors
- Reset `optind` so that we can call `main()` multiple times in a row