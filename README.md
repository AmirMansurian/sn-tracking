# SoccerNet - Tracking

Welcome to the SoccerNet Development Kit for the Tracking Task and Challenge. This kit is meant as a help to get started working with the data and the proposed task. More information about the dataset can be found on our [official website](https://www.soccer-net.org/).

<p align="center"><img src="Images/GraphicalAbstract-tracking.png" width="640"></p>

The Tracking dataset consists of 12 complete soccer games from the main camera including:
 - 200 clips of 30 seconds with tracking data.
 - one complete halftime annotated with tracking data.
 - the complete videos for the 12 games.

Note that a subset of this data is used in this first challenge. In particular, this accounts for 57 30-seconds clips for the train set, 49 clips for the test set, 58 clips for our first public challenge, and 37 clips for our future challenges, including the entire half-time video in the latter.

Participate in our upcoming Challenge at CVPR and try to win up to 1000$ sponsored by [Baidu](https://www.baidu.com/)! All details are available on the [challenge website](https://eval.ai/web/challenges/challenge-page/1539/overview), or on the [main page](https://www.soccer-net.org/).

The participation deadline is fixed at the 30th of May 2022.
The official rules and guidelines are provided in [ChallengeRules.md](ChallengeRules.md).

<a href="https://youtu.be/tA9E1hkiyB0">
<p align="center"><img src="Images/Thumbnail.png" width="720"></p>
</a>

## How to download SoccerNet-tracking

We provide a [SoccerNet pip package](https://pypi.org/project/SoccerNet/) to easily download the data and the annotations. 

To install the pip package simply run:

<code>pip install SoccerNet</code>

Then, to download the tracking data, enter the following commands:

```python
from SoccerNet.Downloader import SoccerNetDownloader
mySoccerNetDownloader = SoccerNetDownloader(LocalDirectory="path/to/SoccerNet")
mySoccerNetDownloader.downloadDataTask(task="tracking", split=["train","test","challenge"])
```

## Data format

The ground truth and detections are stored in comma-separate csv files with 10 columns. 
These values correspond in order to: frame ID, track ID, top left coordinate of the bounding box, top y coordinate, width, height, confidence score for the detection (always 1. for the ground truth) and the remaining values are set to -1 as they are not used in our dataset, but are needed to comply with the MOT20 requirements.

## Task description

Multi-object tracking (MOT) aims at recovering trajectories of multiple objects in time by estimating object bounding boxes and identities in videos sequences. 
We consider two tasks: (1) a pure association task that considers ground-truth detections (task of the first challenge), or (2) a complete tracking task that expects detecting the objects of interest from the raw video (task for benchmarking and future challenges).

So for the first challenge, one may use the provided ground-truth bounding boxes and focus only on the association task.

The object classes are not taken into account in this challenge or the evaluation. The object to retrieve are among the following classes: players, goalkeepers, referees, balls and any other human entering the field.

For our benchmark and challenge, we consider HOTA as the main metric. More specifically, this metric can be decomposed into two components: DetA and AssA, focusing on detection and association accuracy, respectively. 



## Benchmark Implementations

This repository contains several [benchmarks](Benchmarks) for the tracking task. You can use these codes to build upon state-of-the-art methods and improve the performances.

## Evaluation

We use the [TrackEval](https://github.com/JonathonLuiten/TrackEval) repository to evaluate the performances. To participate the challenge, you should submit the result as a zip file to [EvalAI](https://eval.ai/web/challenges/challenge-page/1539/overview). Please see the READMEs of our baseline methods under the "Benchmarks" directory for instructions on how to prepare the zipped results.

## Visualizations

You can use the [MOT Challenge Evaluation Kit](https://github.com/dendorferpatrick/MOTChallengeEvalKit) to visualize the tracks.

## Our other Challenges

Check out our other challenges related to SoccerNet!
- [Action Spotting](https://github.com/SoccerNet/sn-spotting)
- [Replay Grounding](https://github.com/SoccerNet/sn-grounding)
- [Calibration](https://github.com/SoccerNet/sn-calibration)
- [Re-Identification](https://github.com/SoccerNet/sn-reid)
- [Tracking](https://github.com/SoccerNet/sn-tracking)

## Citation
For further information check out the paper and supplementary material:
https://arxiv.org/abs/2210.02365

Please cite our work if you use the SoccerNet dataset:

```bibtex
@inproceedings{cioppa2022soccernet,
  title={SoccerNet-Tracking: Multiple Object Tracking Dataset and Benchmark in Soccer Videos},
  author={Cioppa, Anthony and Giancola, Silvio and Deliege, Adrien and Kang, Le and Zhou, Xin and Cheng, Zhiyu and Ghanem, Bernard and Van Droogenbroeck, Marc},
  booktitle={Proceedings of the IEEE/CVF Conference on Computer Vision and Pattern Recognition},
  pages={3491--3502},
  year={2022}
}
```

```bibtex
@inproceedings{Giancola_2022,
	doi = {10.1145/3552437.3558545},
	url = {https://doi.org/10.1145%2F3552437.3558545},
	year = 2022,
	month = {oct},
	publisher = {{ACM}},
	author = {Silvio Giancola and Anthony Cioppa and Adrien Deli{\`{e}}ge and Floriane Magera and Vladimir Somers and Le Kang and Xin Zhou and Olivier Barnich and Christophe De Vleeschouwer and Alexandre Alahi and Bernard Ghanem and Marc Van Droogenbroeck and Abdulrahman Darwish and Adrien Maglo and Albert Clap{\'{e}}s and Andreas Luyts and Andrei Boiarov and Artur Xarles and Astrid Orcesi and Avijit Shah and Baoyu Fan and Bharath Comandur and Chen Chen and Chen Zhang and Chen Zhao and Chengzhi Lin and Cheuk-Yiu Chan and Chun Chuen Hui and Dengjie Li and Fan Yang and Fan Liang and Fang Da and Feng Yan and Fufu Yu and Guanshuo Wang and H. Anthony Chan and He Zhu and Hongwei Kan and Jiaming Chu and Jianming Hu and Jianyang Gu and Jin Chen and Jo{\~{a}}o V. B. Soares and Jonas Theiner and Jorge De Corte and Jos{\'{e}} Henrique Brito and Jun Zhang and Junjie Li and Junwei Liang and Leqi Shen and Lin Ma and Lingchi Chen and Miguel Santos Marques and Mike Azatov and Nikita Kasatkin and Ning Wang and Qiong Jia and Quoc Cuong Pham and Ralph Ewerth and Ran Song and Rengang Li and Rikke Gade and Ruben Debien and Runze Zhang and Sangrok Lee and Sergio Escalera and Shan Jiang and Shigeyuki Odashima and Shimin Chen and Shoichi Masui and Shouhong Ding and Sin-wai Chan and Siyu Chen and Tallal El-Shabrawy and Tao He and Thomas B. Moeslund and Wan-Chi Siu and Wei Zhang and Wei Li and Xiangwei Wang and Xiao Tan and Xiaochuan Li and Xiaolin Wei and Xiaoqing Ye and Xing Liu and Xinying Wang and Yandong Guo and Yaqian Zhao and Yi Yu and Yingying Li and Yue He and Yujie Zhong and Zhenhua Guo and Zhiheng Li},
	title = {{SoccerNet} 2022 Challenges Results},
	booktitle = {Proceedings of the 5th International {ACM} Workshop on Multimedia Content Analysis in Sports}
}
```


