# Brandon Panuco

## About Me
![Me](myself.jpg) <br>
I am a determined programmer looking to land a software engineering job in the near future and hopefully learn new programming skills along the way!

## Programming Languages
- Java
- C++
- Python
- SQL
- JavaScript

## Teaching Experience
[My Teaching Portfolio](https://sites.google.com/view/brandonpanuco2270/home)

## Research Experience
• Became part of Professor [*Amy Ousterhout’s*](https://amyousterhout.com/) research team to follow up on their previous work “[*Zed: Leveraging 
Data Types to Process Eclectic Data*](https://amyousterhout.com/papers/zed_cidr23.pdf)”.<br>
• My group and I proposed to evaluate the usability of Zed, a new system designed for processing large and 
evolving datasets. As part of our proposed plan, we compared it to the following data models: JSON, SQlite3, 
Asterix DB. Our work is detailed in [*Analyzing the Usability of Zed*](https://drive.google.com/file/d/17z3WmNiFv48jHlLdWhOzZJzW4qMxXx6q/view?usp=sharing).<br>
• During my involvement in our project, I gained the following skills:<br><br>
o Creating bash scripts to process and store homogeneous and heterogeneous data sets<br>
o Use GitHub commands to add, commit, and push our work<br>
o Develop bash scripts to ingest and query data for all data models and to compress and uncompress large 
datasets into GitHub<br>
o Develop python scripts to combine homogeneous data sets into a single heterogeneous data set, test for 
ingestion correctness, and fix syntax issues preventing us from querying or ingesting data<br>
o Use Jq to query JSON data<br>
o Use Zed lakes and ZSON to process Zed and JSON data<br>
o Work with command-line arguments to query SQlite3 databases<br>

## Inspiring Quotes
> "A good programmer is someone who always looks both ways before crossing a one-way street" - Doug Linder<br>
> "People don’t care about what you say, they care about what you build" – Mark Zuckerberg<br>
> "Experience is the name everyone gives to their mistakes" – Oscar Wilde<br>
> "Everyday life is like programming, I guess. If you love something, you can put beauty into it" – Donald Knuth<br>

# My Programmer Bucketlist
- [x] Got envolved in research
- [x] Made new connections
- [x] Learned more programming languages
- [ ] Gained Software engineering skills
- [x] Completed my resume
- [ ] Got an intership
- [x] Improved my work schedule

## Code Snippet using Dijkstra’s Algorithm I Learned
```
vector<tuple<string, string, double>> Graph::shortest_path_weighted(string const& start_label, string const& end_label) {
    unordered_map<string, double> distance;
    priority_queue<pair<double, string>, vector<pair<double, string>>, greater<pair<double, string>>> priorityqueue;
    vector<tuple<string, string, double>> path;
    unordered_map<string, string> parent;

    // immediately return distance -1 if start and end labels are equal
    if (start_label == end_label) {
        path.push_back(make_tuple(start_label, end_label, -1));
        return path;
    }

    for (const auto& node : node_set) {
        // by dijkstra's set to infinity by default
        distance[node] = numeric_limits<double>::infinity();
    }
    // from start set to 0 by dijkstra's
    distance[start_label] = 0;
    priorityqueue.push({ 0, start_label });
    // dijkstra's algorithm
    while (!priorityqueue.empty()) {
        string label1 = priorityqueue.top().second;
        priorityqueue.pop();

        for (const auto& tuple : csv_tuples) {
            string label2;
            double weight;

            if (get<0>(tuple) == label1 || get<1>(tuple) == label1) {
                weight = get<2>(tuple);
                (get<0>(tuple) == label1) ? label2 = get<1>(tuple) : label2 = get<0>(tuple);
            }
            else
                continue;
            
            if (distance[label1] + weight < distance[label2]) {
                distance[label2] = distance[label1] + weight;
                parent[label2] = label1;
                priorityqueue.push({ distance[label2], label2 });
            }
        }
    }

    if (parent.find(end_label) != parent.end()) {
        string node = end_label;
        while (node != start_label) {
            string previous = parent[node];
            path.insert(path.begin(), make_tuple(previous, node, edge_weight(previous, node)));
            node = previous;
        }
    }

    return path;
}
```
# [Back to Top](#My-Programmer-Bucketlist)
