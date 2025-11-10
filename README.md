# VidToMusicTags
[colab link](https://colab.research.google.com/drive/1rAfH-n_y6CUZ8TiqwZitqarVEKF5p69C#scrollTo=6hmqP2xSszM0)
This notebook serves as a prototype for the AI workflow of classifying videos into natural language tags that are compatible with large music publishing libraries and their set of database tags.

Currently, the main problems associated with the current Video to Music Tags workflows is the cost of having to train a vision based model to perform multi-class classification on video frames, which suffers from training and testing costs and lack of flexibility in retroactively choosing different tags to perform classification on.

<div align="center">
	<img src="https://mermaid.ink/img/pako:eNpVkU1rAjEQhv9KSC8WtIi95VDQXQoerKVre8l6GJLZNbhJJB8Ucf3vjUlbMKfMzPO-M5lcqLASKaPdYL_FAVwgu7o1JJ0lX5tTDORLSbR7xpjK4Wz2MjagTwNK8upAox_JarKJQ1DaShjIskcTHovHKuPZgTRRa3DnkVSTagDvVacEBGXNnWL9tuCb6JUgO-j9XVsyvp8lmJBqNQQQN5PUvSrCKiM138Zw47O6VOrZU6psP3cLzitrujSNEUgaYR3uf5nqj3nmPI9DPhC8Ncr0BSlY7lljR8pQPjh7RPbQzed0SjU6DUqmZV6ygoYDamwpS1cJ7tjS1lwTBzHY5mwEZcFFnFJnY3-grIPBpyieJASsFfRpuf9ZlCpYtyl_JW6P6On1BzY2koU?type=png">
</div>

This project ameliorates these issues by utilising a dual stage large language model (LLM) architecture to perform the classification. Video frames are sampled from the input video and fed into a Vision Model, trained specifically on videos, which generates a short and concise summary explaining what is happening.

This video summary is then fed as input to a second LLM stage which will generate a json payload with a list of tags the model classifies this summary as, along with a confidence score for each identified tag. The json payload also features a quick paragraph detailing the reasoning behind the choices made along with important information found within the summary.

The main benefits of this approach comes to its flexibility in choice of music tags. Tags can be freely added or removed and written in natural language as well without the need to retrain a model. This is because one can leverage the classification agent's reasoning capabilities to accurately perform the classification. In addition, further semantic context can be provided to each tag to help provide the agent with additional meaning, leading to more accurate results, at the cost of additional prompt tokens consumed


-----------
