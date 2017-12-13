# fastText

[fastText](https://fasttext.cc/) 自然言語ライブラリ    

## Requirements

**fastText** mac OSかLinuxでのビルド
C++11をサポート

* (gcc-4.6.3 or newer) or (clang-3.3 or newer)
* python 2.6 or newer
* numpy & scipy

## Building fastText

```
$ git clone https://github.com/miyamotok0105/fastText_ja.git
$ cd fastText_ja
$ make
```

## Example use cases

### ニュース分類

rondhuit datasetよりニュースコーパスをダウンロード。    
https://www.rondhuit.com/download.html    

分類しにくそうなカテゴリを削った。    

```
it-life-hack
__label__1
movie-enter
__label__2
peachy
__label__3
sports-watch
__label__4
```

```
$ ./fasttext supervised -input livedoordic_fasttext.txt -output livedoor_model
$ ./fasttext supervised -input livedoor_test_c4.txt -output livedoor_model -lr 0.15 -dim 10 -bucket 10000
$ ./fasttext test livedoor_model.bin livedoor_test_c4.txt
```


## Full documentation

Invoke a command without arguments to list available arguments and their default values:

```
$ ./fasttext supervised
Empty input or output path.

The following arguments are mandatory:
  -input              training file path
  -output             output file path

  The following arguments are optional:
  -verbose            verbosity level [2]

  The following arguments for the dictionary are optional:
  -minCount           minimal number of word occurences [5]
  -minCountLabel      minimal number of label occurences [0]
  -wordNgrams         max length of word ngram [1]
  -bucket             number of buckets [2000000]
  -minn               min length of char ngram [3]
  -maxn               max length of char ngram [6]
  -t                  sampling threshold [0.0001]
  -label              labels prefix [__label__]

  The following arguments for training are optional:
  -lr                 learning rate [0.05]
  -lrUpdateRate       change the rate of updates for the learning rate [100]
  -dim                size of word vectors [100]
  -ws                 size of the context window [5]
  -epoch              number of epochs [5]
  -neg                number of negatives sampled [5]
  -loss               loss function {ns, hs, softmax} [ns]
  -thread             number of threads [12]
  -pretrainedVectors  pretrained word vectors for supervised learning []
  -saveOutput         whether output params should be saved [0]

  The following arguments for quantization are optional:
  -cutoff             number of words and ngrams to retain [0]
  -retrain            finetune embeddings if a cutoff is applied [0]
  -qnorm              quantizing the norm separately [0]
  -qout               quantizing the classifier [0]
  -dsub               size of each sub-vector [2]
```


## Resources

You can find the preprocessed YFCC100M data used in [2] at https://research.facebook.com/research/fasttext/

Pre-trained word vectors for 294 languages are available [*here*](https://github.com/facebookresearch/fastText/blob/master/pretrained-vectors.md).


## License

fastText is BSD-licensed. We also provide an additional patent grant.
