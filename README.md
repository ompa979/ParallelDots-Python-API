ParallelDots-Python-API
=======================

A wrapper for the [ParallelDots APIs](http://www.paralleldots.com).

Build Status: [![CircleCI](https://circleci.com/gh/ParallelDots/ParallelDots-Python-API.svg?style=svg)](https://circleci.com/gh/ParallelDots/ParallelDots-Python-API)

Installation
------------
From PyPI:

	pip install paralleldots


From Source:

	https://github.com/ParallelDots/ParallelDots-Python-API.git
	python setup.py install

API Keys & Setup
----------------
Sign up to create your free account from [ParallelDots](https://www.paralleldots.com/sign-up).
[Log in](https://user.apis.paralleldots.com/login) to your account to get your API key.

Configuration:

	>>>>> import paralleldots

	# Setting your API key
	>>>>> paralleldots.set_api_key( "YOUR API KEY" )

	# Viewing your API key
	>>>>> paralleldots.get_api_key()

Languages Supported:
-------------------

- Portuguese ( pt )
- Chinese ( zh )
- Spanish ( es )
- German ( de )
- French ( fr )
- Dutch ( nl )
- Italian (it)
- Japanese ( ja )
- Indonesian ( id )
- Thai ( th )
- Danish ( da )
- Finish ( fi )

Supported APIs:
---------------

- Abuse
- Custom Classifier
- Emotion
- Facial Emotion
- Intent
- Keywords
- Multilanguage Keywords ( Supports Multiple Languages )
- Named Entity Extraction/Recognition ( NER )
- Not Safe For Work ( NSFW Image Classifier )
- Phrase Extractor
- Popularity ( Image Classifier )
- Object Recognizer
- Sentiment Analysis
- Semantic Similarity
- Taxonomy
- Text Parser
- Usage

Examples
--------

	>>> import paralleldots

	>>> api_key   = "xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx"
	>>> text      = "Prime Minister Narendra Modi tweeted a link to the speech Human Resource Development Minister Smriti Irani made in the Lok Sabha during the bate on the ongoing JNU row and the suicide of Dalit scholar Rohith Vemula at the Hyderabad Central University."
	>>> path      = "/home/my_computer/Downloads/image_1.jpg"
	>>> lang_code = "fr"
	>>> lang_text = "C'est un environnement très hostile, si vous choisissez de débattre ici, vous serez vicieusement attaqué par l'opposition."
	>>> category  = { "finance": [ "markets", "economy", "shares" ], "world politics": [ "diplomacy", "UN", "war" ], "india": [ "congress", "india", "bjp" ] }
	>>> url       = "http://i.imgur.com/klb812s.jpg"


	>>> paralleldots.set_api_key( api_key )
	>>> print( "API Key: %s" % paralleldots.get_api_key() )

	>>> print( "\nAbuse" )
	>>> print( abuse( text ) )
	{"usage":"By accessing ParallelDots API or using information generated by ParallelDots API, you are agreeing to be bound by the ParallelDots API Terms of Use: http://www.paralleldots.com/terms-and-conditions", "sentence_type":"Non Abusive", "confidence_score":0.876953}

	>>> print( "\nCustom Classifier" )
	>>> print( custom_classifier( text, category ) )
	{"usage":"By accessing ParallelDots API or using information generated by ParallelDots API, you are agreeing to be bound by the ParallelDots API Terms of Use: http://www.paralleldots.com/terms-and-conditions", "taxonomy":[{"tag":"world politics", "confidence_score":0.580833}, {"tag":"finance", "confidence_score":0.259185}]}

	>>> print( "\nEmotion" )
	>>> print( emotion( text ) )
	{"emotion":{"emotion":"Happy", "probabilities":{"Sarcasm":0.0, "Angry":0.04090321436524391, "Sad":0.0, "Fear":0.0, "Bored":0.0, "Excited":0.07638891041278839, "Happy":0.1223890483379364}}, "usage":"By accessing ParallelDots API or using information generated by ParallelDots API, you are agreeing to be bound by the ParallelDots API Terms of Use: http://www.paralleldots.com/terms-and-conditions"}

	>>> print( "\nEmotion - Lang: Fr". )
	>>> print( emotion( lang_text, lang_code ) )
	{"emotion":{"emotion":"Angry", "probabilities":{"Sarcasm":0.052613839507102966, "Angry":0.07304570078849792, "Sad":0.051657479256391525, "Fear":0.07096020132303238, "Bored":0.0, "Excited":0.0, "Happy":0.0}}, "usage":"By accessing ParallelDots API or using information generated by ParallelDots API, you are agreeing to be bound by the ParallelDots API Terms of Use: http://www.paralleldots.com/terms-and-conditions"}

	>>> print( "\nFacial Emotion" )
	>>> print( facial_emotion( path ) )
	{"usage":"By accessing ParallelDots API or using information generated by ParallelDots API, you are agreeing to be bound by the ParallelDots API Terms of Use: http://www.paralleldots.com/terms-and-conditions", "output":"No face detected."}

	>>> print( "\nFacial Emotion: URL Method" )
	>>> print( facial_emotion_url( url ) )
	{"facial_emotion":[{"score":0.439317524433136, "tag":"Angry"}, {"score":0.18545667827129364, "tag":"Surprise"}, {"score":0.11217296868562698, "tag":"Sad"}, {"score":0.08146321028470993, "tag":"Neutral"}, {"score":0.06052987277507782, "tag":"Happy"}, {"score":0.06052987277507782, "tag":"Fear"}, {"score":0.06052987277507782, "tag":"Disgust"}], "usage":"By accessing ParallelDots API or using information generated by ParallelDots API, you are agreeing to be bound by the ParallelDots API Terms of Use: https://www.paralleldots.com/terms-and-conditions"}

	>>> print( "\nIntent" )
	>>> print( intent( text ) )
	{"probabilities":{"marketing":0.042, "spam/junk":0.003, "news":0.927, "feedback/opinion":0.024, "query":0.004}, "usage":"By accessing ParallelDots API or using information generated by ParallelDots API, you are agreeing to be bound by the ParallelDots API Terms of Use: http://www.paralleldots.com/terms-and-conditions", "intent":"news"}

	>>> print( "\nKeywords" )
	>>> print( keywords( text ) )
	{"keywords":[{"keyword":"Prime Minister Narendra Modi", "confidence_score":0.857594}, {"keyword":"link", "confidence_score":0.913924}, {"keyword":"speech Human Resource", "confidence_score":0.70655}, {"keyword":"Smriti", "confidence_score":0.860351}, {"keyword":"Lok", "confidence_score":0.945534}], "usage":"By accessing ParallelDots API or using information generated by ParallelDots API, you are agreeing to be bound by the ParallelDots API Terms of Use: http://www.paralleldots.com/terms-and-conditions"}

	>>> print( "\nLanguage Detection" )
	>>> print( language_detection( lang_text ) )
	{"usage":"By accessing ParallelDots API or using information generated by ParallelDots API, you are agreeing to be bound by the ParallelDots API Terms of Use: http://www.paralleldots.com/terms-and-conditions", "output":"French", "code":200, "prob":0.9999592304229736}

	>>> print( "\nMultilang Keywords - Lang: Fr". )
	>>> print( multilang_keywords( lang_text, lang_code ) )
	{"keywords":["cest", "très", "vicieusement", "attaqué", "hostile", "environnement", "débattre", "choisissez", "lopposition", "si"], "usage":"By accessing ParallelDots API or using information generated by ParallelDots API, you are agreeing to be bound by the ParallelDots API Terms of Use: http://www.paralleldots.com/terms-and-conditions"}

	>>> print( "\nNER" )
	>>> print( ner( text ) )
	{"usage":"By accessing ParallelDots API or using information generated by ParallelDots API, you are agreeing to be bound by the ParallelDots API Terms of Use: http://www.paralleldots.com/terms-and-conditions", "entities":[{"category":"name", "name":"Narendra Modi", "confidence_score":0.990574}, {"category":"name", "name":"Smriti Irani", "confidence_score":0.989922}, {"category":"name", "name":"Rohith Vemula", "confidence_score":0.839291}, {"category":"group", "name":"Lok Sabha", "confidence_score":0.80819}, {"category":"group", "name":"Dalit", "confidence_score":0.655424}, {"category":"group", "name":"Central University", "confidence_score":0.708817}, {"category":"place", "name":"Hyderabad", "confidence_score":0.591985}]}

	>>> print( "\nNSFW" )
	>>> print( nsfw( path ) )
	{"usage":"By accessing ParallelDots API or using information generated by ParallelDots API, you are agreeing to be bound by the ParallelDots API Terms of Use: http://www.paralleldots.com/terms-and-conditions", "output":"not safe to open at work", "prob":0.9995405673980713}

	>>> print( "\nNSFW: URL Method" )
	>>> print( nsfw_url( url ) )
	{"usage":"By accessing ParallelDots API or using information generated by ParallelDots API, you are agreeing to be bound by the ParallelDots API Terms of Use: https://www.paralleldots.com/terms-and-conditions", "output":"safe to open at work", "prob":0.979527473449707}

	>>> print( "\nObject Recognizer" )
	>>> print( object_recognizer( path ) )
	{"usage":"By accessing ParallelDots API or using information generated by ParallelDots API, you are agreeing to be bound by the ParallelDots API Terms of Use: http://www.paralleldots.com/terms-and-conditions", "output":[{"score":0.8445611596107483, "tag":"Muscle"}, {"score":0.6443125605583191, "tag":"Limb"}, {"score":0.5493743419647217, "tag":"Arm"}, {"score":0.5155590772628784, "tag":"Person"}, {"score":0.39905625581741333, "tag":"Human body"}, {"score":0.39764025807380676, "tag":"Leg"}, {"score":0.3255367875099182, "tag":"Hand"}, {"score":0.2798691689968109, "tag":"Male person"}, {"score":0.25423258543014526, "tag":"Adult"}, {"score":0.2470093071460724, "tag":"Man"}]}

	>>> print( "\nObject Recognizer: URL Method" )
	>>> print( object_recognizer_url( url ) )
	{"usage":"By accessing ParallelDots API or using information generated by ParallelDots API, you are agreeing to be bound by the ParallelDots API Terms of Use: https://www.paralleldots.com/terms-and-conditions", "output":[{"score":0.8752718567848206, "tag":"Dog"}, {"score":0.8702095746994019, "tag":"Pet"}, {"score":0.8646901249885559, "tag":"Mammal"}, {"score":0.8270695209503174, "tag":"Animal"}, {"score":0.2900576591491699, "tag":"Snow"}, {"score":0.22053982317447662, "tag":"Winter"}, {"score":0.1604217290878296, "tag":"Dog breed"}, {"score":0.14872552454471588, "tag":"Carnivore"}, {"score":0.08632490038871765, "tag":"Puppy"}, {"score":0.07958601415157318, "tag":"Wildlife"}]}

	>>> print( "\nPhrase Extractor" )
	>>> print( phrase_extractor( text ) )
	{"keywords":[{"relevance_score":3, "keyword":"Hyderabad Central University"}, {"relevance_score":2, "keyword":"Rohith Vemula"}, {"relevance_score":2, "keyword":"JNU row"}, {"relevance_score":6, "keyword":"Human Resource Development Minister Smriti Irani"}, {"relevance_score":2, "keyword":"Lok Sabha"}, {"relevance_score":4, "keyword":"Prime Minister Narendra Modi"}, {"relevance_score":2, "keyword":"Dalit scholar"}], "usage":"By accessing ParallelDots API or using information generated by ParallelDots API, you are agreeing to be bound by the ParallelDots API Terms of Use: http://www.paralleldots.com/terms-and-conditions"}

	>>> print( "\nPopularity" )
	>>> print( popularity( path ) )
	{"Popular":"38.1271243095", "usage":"By accessing ParallelDots API or using information generated by ParallelDots API, you are agreeing to be bound by the ParallelDots API Terms of Use: http://www.paralleldots.com/terms-and-conditions", "Not Popular":"61.8728756905"}

	>>> print( "\nPopularity: URL Method" )
	>>> print( popularity_url( url ) )
	{"Popular":"68.9268052578", "usage":"By accessing ParallelDots API or using information generated by ParallelDots API, you are agreeing to be bound by the ParallelDots API Terms of Use: https://www.paralleldots.com/terms-and-conditions", "Not Popular":"31.0731947422"}

	>>> print( "\nSentiment" )
	>>> print( sentiment( text ) )
	{"probabilities":{"positive":0.266, "neutral":0.549, "negative":0.185}, "usage":"By accessing ParallelDots API or using information generated by ParallelDots API, you are agreeing to be bound by the ParallelDots API Terms of Use: http://www.paralleldots.com/terms-and-conditions", "sentiment":"neutral"}

	>>> print( "\nSentiment - Lang: Fr". )
	>>> print( sentiment( lang_text, lang_code ) )
	{"probabilities":{"positive":0.02, "neutral":0.291, "negative":0.689}, "usage":"By accessing ParallelDots API or using information generated by ParallelDots API, you are agreeing to be bound by the ParallelDots API Terms of Use: http://www.paralleldots.com/terms-and-conditions", "sentiment":"negative"}

	>>> print( "\nSimilarity" )
	>>> print( similarity( "I love fish and ice cream!", "fish and ice cream are the best!" ) )
	{"usage":"By accessing ParallelDots API or using information generated by ParallelDots API, you are agreeing to be bound by the ParallelDots API Terms of Use: http://www.paralleldots.com/terms-and-conditions", "actual_score":0.848528, "normalized_score":4.936506}

	>>> print( "\nTaxonomy" )
	>>> print( taxonomy( text ) )
	{"usage":"By accessing ParallelDots API or using information generated by ParallelDots API, you are agreeing to be bound by the ParallelDots API Terms of Use: http://www.paralleldots.com/terms-and-conditions", "taxonomy":[{"tag":"News and Politics/Law", "confidence_score":0.845402}, {"tag":"Hobbies & Interests/Workshops and Classes", "confidence_score":0.878964}, {"tag":"Business and Finance/Industries", "confidence_score":0.7353}]}

	>>> print( "\nText Parser" )
	>>> print( text_parser( text ) )
	{"usage":"By accessing ParallelDots API or using information generated by ParallelDots API, you are agreeing to be bound by the ParallelDots API Terms of Use: http://www.paralleldots.com/terms-and-conditions", "output":[{"text":"Prime", "Dependency":"compound", "Tags":"noun"}, {"text":"Minister", "Dependency":"compound", "Tags":"noun"}, {"text":"Narendra", "Dependency":"compound", "Tags":"noun"}, {"text":"Modi", "Dependency":"nominal subject", "Tags":"noun"}, {"text":"tweeted", "Dependency":"root", "Tags":"verb"}, {"text":"a", "Dependency":"determiner", "Tags":"determiner"}, {"text":"link", "Dependency":"direct object", "Tags":"noun"}, {"text":"to", "Dependency":"prepositional modifier", "Tags":"preposition or conjunction"}, {"text":"the", "Dependency":"determiner", "Tags":"determiner"}, {"text":"speech", "Dependency":"compound", "Tags":"noun"}, {"text":"Human", "Dependency":"compound", "Tags":"noun"}, {"text":"Resource", "Dependency":"compound", "Tags":"noun"}, {"text":"Development", "Dependency":"compound", "Tags":"noun"}, {"text":"Minister", "Dependency":"compound", "Tags":"noun"}, {"text":"Smriti", "Dependency":"compound", "Tags":"noun"}, {"text":"Irani", "Dependency":"object of a preposition", "Tags":"noun"}, {"text":"in", "Dependency":"prepositional modifier", "Tags":"preposition or conjunction"}, {"text":"the", "Dependency":"determiner", "Tags":"determiner"}, {"text":"Lok", "Dependency":"compound", "Tags":"noun"}, {"text":"Sabha", "Dependency":"object of a preposition", "Tags":"noun"}, {"text":"during", "Dependency":"prepositional modifier", "Tags":"preposition or conjunction"}, {"text":"the", "Dependency":"determiner", "Tags":"determiner"}, {"text":"debate", "Dependency":"object of a preposition", "Tags":"noun"}, {"text":"on", "Dependency":"prepositional modifier", "Tags":"preposition or conjunction"}, {"text":"the", "Dependency":"determiner", "Tags":"determiner"}, {"text":"ongoing", "Dependency":"adjectival modifier", "Tags":"adjective"}, {"text":"JNU", "Dependency":"compound", "Tags":"noun"}, {"text":"row", "Dependency":"object of a preposition", "Tags":"noun"}, {"text":"and", "Dependency":"coordinating conjunction", "Tags":"conjuction"}, {"text":"the", "Dependency":"determiner", "Tags":"determiner"}, {"text":"suicide", "Dependency":"conjunct", "Tags":"noun"}, {"text":"of", "Dependency":"prepositional modifier", "Tags":"preposition or conjunction"}, {"text":"Dalit", "Dependency":"compound", "Tags":"noun"}, {"text":"scholar", "Dependency":"compound", "Tags":"noun"}, {"text":"Rohith", "Dependency":"compound", "Tags":"noun"}, {"text":"Vemula", "Dependency":"object of a preposition", "Tags":"noun"}, {"text":"at", "Dependency":"prepositional modifier", "Tags":"preposition or conjunction"}, {"text":"the", "Dependency":"determiner", "Tags":"determiner"}, {"text":"Hyderabad", "Dependency":"compound", "Tags":"noun"}, {"text":"Central", "Dependency":"compound", "Tags":"noun"}, {"text":"University", "Dependency":"object of a preposition", "Tags":"noun"}]}

	>>> usage()
	{ "paying": False, "visual_monthly_quota": 100, "visual_daily_quota": 1000, "monthly_quota": 10000, "daily_quota": 1000, "excel_monthly_quota": 1000, "excel_daily_quota": 100 }