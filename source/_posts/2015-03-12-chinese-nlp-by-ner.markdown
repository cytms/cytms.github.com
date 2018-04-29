---
layout: post
title: "Chinese NLP by NER (java)"
date: 2015-03-12 11:45
comments: true
categories: Text Mining
---

[[NER]](http://nlp.stanford.edu/software/CRF-NER.shtml) 是 stanford 所提供的一個 Natural Language Processing 套件，現在就讓歪踢帶你快速上手他的 API 。

<!--More-->
中文跟英文不一樣，字字相連在一起，所以你要使用NER以前，必須先對你的input做segmentation。而 stanford 就提供了他們自己的斷字 API - [Stanford Word Segmenter](http://nlp.stanford.edu/software/segmenter.shtml)，你只要下載檔案、加 jar 檔到你的project中就可以輕鬆斷字。

接下來就是範例程式：
{% codeblock %}
import edu.stanford.nlp.ie.AbstractSequenceClassifier;
import edu.stanford.nlp.ling.CoreLabel;
import edu.stanford.nlp.ling.CoreAnnotations;
import edu.stanford.nlp.util.StringUtils;
import edu.stanford.nlp.util.Triple;
import java.io.PrintStream;
import java.io.UnsupportedEncodingException;
import java.util.List;
import java.util.Properties;

import edu.stanford.nlp.ie.crf.CRFClassifier;

public class NERDemo {
	private static final String basedir = 
		System.getProperty("SegDemo", "stanford-segmenter-2015-01-30/data");

	public static void main(String[] args) throws Exception {

		String serializedClassifier = 
				"stanford-ner-2015-01-30/classifiers/chinese.misc.distsim.crf.ser.gz";

		AbstractSequenceClassifier<CoreLabel> classifier = 
				CRFClassifier.getClassifier(serializedClassifier);

		String sample = "徐佳青表示，思慮不週造成這樣的結果，非她本意，也因有愧發言人職責，昨天即辭發言人以示負責。" +
				"希望不要因這個事件，讓社會更值得被討論的重要事情失焦。她會深切虛心反省，也會秉持初衷，堅持信仰價值。" + 
				"感謝各位關心與指教。";

		String fileContents = getSeg(sample);
		System.out.println(fileContents);

		List<List<CoreLabel>> out = classifier.classify(fileContents);
		System.out.println(out);
		for (List<CoreLabel> sentence : out) {
			for (CoreLabel word : sentence) {
				System.out.print(word.word() + '/'
						+ word.get(CoreAnnotations.AnswerAnnotation.class)
						+ ' ');
			}
			System.out.println();
		}
	}

	private static String getSeg(String sample) {
		try {
			System.setOut(new PrintStream(System.out, true, "utf-8"));
		} catch (UnsupportedEncodingException e) {
			e.printStackTrace();
		}

		Properties props = new Properties();
		props.setProperty("sighanCorporaDict", basedir);
		// below is needed because CTBSegDocumentIteratorFactory accesses it
		props.setProperty("serDictionary", basedir + "/dict-chris6.ser.gz");
		props.setProperty("inputEncoding", "UTF-8");
		props.setProperty("sighanPostProcessing", "true");

		CRFClassifier<CoreLabel> segmenter = new CRFClassifier<CoreLabel>(props);
		segmenter.loadClassifierNoExceptions(basedir + "/ctb.gz", props);

		// ZHConverter converter = ZHConverter.getInstance(ZHConverter.SIMPLIFIED);
		// ZHConverter.getInstance(ZHConverter.SIMPLIFIED);
		// sample = converter.convert(sample);
		List<String> segmented = segmenter.segmentString(sample);
		System.out.println(StringUtils.join(segmented));
		return StringUtils.join(segmented);
	}
}

{% endcodeblock %}

`word.get(CoreAnnotations.AnswerAnnotation.class)`取得的就是該詞彙的屬性。有鑑於此標註系統是由簡體中文 train 出來的，各位大大如果不嫌棄的話可以先將繁體字使用[[ZHConverter]](https://code.google.com/p/java-zhconverter/)轉乘簡體中文，再來使用此系統，performance 說不定會好一些些。