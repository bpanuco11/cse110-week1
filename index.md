# Brandon Panuco

## About Me
I am a determined programmer looking to land a software engineering job in the near future and hopefully learn new programming skills along the way!

## Programming Languages
- Java
- C++
- Python
- SQL
- JavaScript

## Inspiring Quotes
> "A good programmer is someone who always looks both ways before crossing a one-way street" - Doug Linder<br>
> "People don’t care about what you say, they care about what you build" – Mark Zuckerberg<br>
> "Experience is the name everyone gives to their mistakes" – Oscar Wilde<br>
> "Everyday life is like programming, I guess. If you love something, you can put beauty into it" – Donald Knuth<br>

## My Goals for The Future

## Code using Dijkstra’s Algorithm I Learned
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

