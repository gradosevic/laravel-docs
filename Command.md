# Progress Bar

```$n = 4000;
$bar = $this->output->createProgressBar($n);;
$bar->start();
while($n > 0){
    $n--;
    $bar->advance();
}
$bar->finish();
```
