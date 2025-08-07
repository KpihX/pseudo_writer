# ✍️ PseudoWriter (Python): A Markov Chain Text Generator

This project is distributed under the [MIT License](LICENSE).

PseudoWriter is a Python program that generates new text in the style of a source text. It uses a simple but powerful statistical model known as a Markov chain. By analyzing the sequence of words in a provided text, it can create new, pseudo-random "chapters" that often capture the tone, vocabulary, and rhythm of the original author.

## 🧠 The Core Concept: Markov Chains

The principle behind PseudoWriter is to model language as a sequence of probabilistic events. Instead of looking at the entire text at once, a Markov model looks at a small, fixed-size window of words, called a **prefix**.

1. **📚 Learning Phase**: The program reads the source text and builds a statistical map. For every unique prefix of length `n` that it finds, it records all the words that immediately follow that prefix.

   * For example, with a prefix length of 2, if the text contains "the cat sat on the mat", the program learns:
     * After `("the", "cat")`, the word `"sat"` can appear.
     * After `("cat", "sat")`, the word `"on"` can appear.
     * ...
2. **✍️ Generation Phase**: To create new text, the program starts with an initial prefix (e.g., two "start" markers). It then:

   * Looks up this prefix in its statistical map.
   * Chooses one of the possible following words at random.
   * Prints the chosen word.
   * Updates the prefix by dropping the first word and adding the newly chosen one.
   * Repeats the process.

### ✨ The Magic of Memory (Prefix Length)

The **prefix length** (the `n` parameter) is the most important setting. It determines the "memory" of the generator:

* **Small `n` (e.g., 1 or 2)**: The generator has very little context. The text will be grammatically messy and nonsensical, but it will use the right vocabulary. It's fascinating how, at first glance, the generated text might appear coherent, but a closer look reveals its lack of true meaning or logical flow, especially with smaller `n` values.
* **Large `n` (e.g., 4 or 5)**: The generator has a much deeper memory. It can remember longer phrases and sentence structures, leading to text that is surprisingly coherent and stylistically similar to the original. It can even generate entire sentences copied directly from the source text if that sequence is the only one it knows for a given prefix.

## 🚀 How to Run This Project

This project is implemented as a Jupyter Notebook, making it interactive and easy to follow.

### Prerequisites

* Python 3.x
* Jupyter Notebook or JupyterLab
* `numpy` library (`pip install numpy`)

### Running the Notebook

1. **Clone the Repository:** If you haven't already, clone the `pseudoWriter` repository from GitHub.
   ```bash
   git clone https://github.com/KpihX/pseudoWriter.git
   cd pseudoWriter/pseudo_writer
   ```
2. **Open with Jupyter:** Launch Jupyter Notebook or JupyterLab in this directory and open `Pseudo_Writer.ipynb`.
3. **Run Cells:** Execute the cells sequentially. The notebook will guide you through the data loading, model learning, and text generation steps. The generated text will be printed to the output and saved as a new `.txt` file in the `miserables/` directory.

### 📜 Example Output (with `n=4`)

Here is an example of output generated from *Les Misérables*. Notice how the sentences flow logically and maintain Victor Hugo's descriptive style, even though they are algorithmically generated:

> ```
> Paris a un enfant et la forêt a un oiseau ; l’oiseau s’appelle le moineau ; l’enfant s’appelle le gamin. <PAR> Accouplez ces deux idées qui contiennent, l’une toute la fournaise, l’autre toute l’aurore, choquez ces étincelles, Paris, l’enfance ; il en jaillit un petit être. Homuncio, dirait Plaute. <PAR> Ce petit être est joyeux. Il ne mange pas tous les jours. Je venais d’Ailly, je marchais dans le pays après une ondée qui avait fait la campagne toute jaune, même que les mares débordaient et qu’il ne sortait plus des sables que de petits brins d’herbe au bord de la Dyle, quatre cachots de pierre, moitié sous terre, moitié sous l’eau. <PAR> C’étaient des in-pace. Chacun de ces cachots a un reste de porte de fer, une latrine, et une lucarne grillée qui, dehors, est à deux pieds au-dessus de la rivière, et, dedans, à six pieds au-dessus du sol. Quatre pieds de rivière coulent extérieurement le long du mur. Le sol est toujours mouillé. L’habitant de l’in-pace avait pour lit cette terre mouillée. Dans l’un des cachots, il y a un moi dans l’infini d’en haut comme il y a un tronçon de carcan scellé au mur ; dans un autre on voit une espèce de boîte carrée faite de quatre lames de granit, trop courte pour qu’on s’y couche, trop basse pour qu’on s’y dresse. On mettait là dedans un être avec un couvercle de pierre par-dessus. Cela est. On le voit. On le touche. Ces in-pace, ces cachots, ces gonds de fer, ces carcans, cette haute lucarne au ras de laquelle coule la rivière, cette boîte de pierre fermée d’un couvercle de granit comme une tombe, avec cette différence qu’ici le mort était un vivant, ce sol qui est de la providence. La geôle étant en mauvais état, monsieur le juge d’instruction trouve à propos de faire transférer Champmathieu à Arras où est la prison départementale. Dans cette prison d’Arras, il y a un maréchal ; mais c’est égal, il faudra bien un bon quart d’heure. En ligne droite, par le fourré, qui est là singulièrement épais, très épineux et très agres...
> ```

## 🎨 Using Your Own Text

You can easily train the generator on any text you like.

1. **Create a new directory** inside the `pseudo_writer/` folder (e.g., `pseudo_writer/my_text/`).
2. **Prepare your source text**: It must be plain text (`.txt`). For best results, split your text into multiple smaller files (e.g., chapters or sections). The program will read all `.txt` files in the directory you provide.
3. **Formatting**: The program reads words based on whitespace. To mark a paragraph break, simply insert the special marker `<PAR>` on its own line or surrounded by spaces.
4. **Modify `novel` variable**: In the first code cell of `Pseudo_Writer.ipynb`, change the `novel` variable to point to your new directory (e.g., `novel = "my_text"`).

## 🤝 Contributing

Contributions are welcome! Feel free to open issues or submit pull requests.

## 🔗 Project Repository

Explore the full project, including the Java implementation, on GitHub:

[https://www.github.com/KpihX/pseudo_writer](https://www.github.com/KpihX/pseudo_writer)

Happy generating! 🤖✍️
