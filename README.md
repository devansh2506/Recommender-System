# Recommender-System
This project implements a course recommender system that suggests relevant courses based on a user’s skills, interests, and career goals. The system collects three inputs from the user: current skills, personal interests, and a target career. These inputs are combined into a single “user profile” text. Meanwhile, each course in the dataset is represented by its title and prerequisites. Both the user profile and course texts are preprocessed and transformed into semantic embeddings using a pre-trained SentenceTransformer model. A similarity search (via FAISS) is then performed to find the five courses whose embeddings are closest to the user profile. The result is a ranked list of the top-5 recommended courses (by relevance), each accompanied by its course title and rating.

## Architecture

Input Collection: The program prompts the user to enter three comma-separated values: current skills, interests, and career goal.

Text Preprocessing: The inputs are concatenated into a single string and cleaned using a transform_text function (e.g., lowercasing, removing punctuation). Similarly, each course’s title and prerequisites are combined into one string and preprocessed.

Embedding Generation: Both the user profile text and each course text are converted into numerical embeddings using the all-MiniLM-L6-v2 SentenceTransformer model. This captures the semantic meaning of the texts.

Indexing with FAISS: All course embeddings are added to a FAISS index (flat index with L2 distance). The user profile embedding is then queried against this index to find the nearest neighbors.

Similarity Computation: FAISS returns the courses with the smallest L2 (Euclidean) distances to the user embedding. Because our embeddings are normalized, these distances correspond to cosine similarity. The five courses with the lowest distances (highest similarity) are selected.

Output: The system retrieves the titles and ratings of the top-5 matching courses from the dataset. It then displays each course title along with its rating, sorted by relevance.

## Results

Relevance: The recommended courses closely match the user’s profile. In the example, courses on machine learning and data science were prioritized. This shows that semantic similarity effectively captures the alignment between user interests and course content.

Scoring: Alongside each course, the rating (from the dataset) is shown. High-rated courses indicate quality and relevance.

Efficiency: Using FAISS for nearest-neighbor search makes recommendation quick even with large course datasets. The combination of modern embeddings and FAISS indexing yields accurate and fast recommendations.

Overall, the system outputs a concise, ranked list of five courses tailored to the user’s inputs. Each recommended course is presented with its title and rating, helping the user to easily compare and select courses.

## Acknowledgements

Sentence Transformers: I used the all-MiniLM-L6-v2 model from the Sentence-Transformers library (by Hugging Face) for generating text embeddings.

FAISS: The FAISS library (from Facebook AI Research) provides efficient similarity search for our course embeddings.

Open-Source Examples: This project is inspired by existing open-source projects and tutorials on course recommendation and NLP pipelines. I thank the developers of these resources and the maintainers of the required libraries.

## Input 
![image](https://github.com/user-attachments/assets/ec21c2da-25a6-41c7-aa55-f2c8711831c5)

## Output
![image](https://github.com/user-attachments/assets/0cdfc17e-d126-48e1-a23b-339c52c90066)


