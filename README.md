# Swift Controls Basic UITableView

**UITableView controla o objeto de interface responsável por exibir uma lista hierárquica de informações. Por ser uma subclasse de UIScrollView, o objeto já possui nativamente a opção de rolagem para seu conteúdo.**

@IBOutlet weak var tableView: UITableView!

var arrayDados = ["Objeto1", "Objeto2", "Objeto3", "Objeto4", "Objeto5"]


override func viewDidLoad() {
    super.viewDidLoad()

    self.tableView.dataSource = self
    self.tableView.delegate = self
}

////////////////////////////////////////////
// MARK: UITableViewDelegate
////////////////////////////////////////////

func numberOfSections(in tableView: UITableView) -> Int {

    return 1
    
}

////////////////////////////////////////////
// MARK: UITableViewDataSource
////////////////////////////////////////////

func tableView(_ tableView: UITableView, numberOfRowsInSection section: Int) -> Int {
    
    return self.arrayDados.count
}

func tableView(_ tableView: UITableView, cellForRowAt indexPath: IndexPath) -> UITableViewCell {
    
    let cell = tableView.dequeueReusableCell(withIdentifier: "celula", for: indexPath)
    
    // Configure the cell...
    cell.textLabel?.text = self.arrayDados[indexPath.row]
    
    return cell
    
}

func tableView(_ tableView: UITableView, didSelectRowAt indexPath: IndexPath) {
    
    print(indexPath.row)
    
}
