class TreeStore:
    def __init__(self, items):
        self.mid = None
        self.end = None
        self.start = None
        self.items = items

    def getAll(self):
        return items

    def getItem(self, id):
        items = []
        items.extend(self.items)
        self.start = 0
        self.end = len(items) - 1
        self.mid = 0
        while self.end >= self.start:
            self.mid = (self.end + self.start) // 2
            if items[self.mid].get('id') == id:
                return items[self.mid]
            elif items[self.mid].get('id') > id:
                self.end -= 1
            elif items[self.mid].get('id') < id:
                self.end += 1

    def getChildren(self, parent_id):
        items = []
        items.extend(self.items)
        self.start = 0
        self.end = len(items) - 1
        self.mid = 0
        parents_list = []
        try:
            while self.end >= self.start:
                self.mid = (self.end + self.start) // 2
                if items[self.mid].get('parent') == parent_id:
                    parents_list.append(items[self.mid])
                    items.pop(self.mid)
                elif items[self.mid].get('parent') > parent_id:
                    self.end -= 1
                elif items[self.mid].get('parent') < parent_id:
                    self.end += 1
        except IndexError:
            pass
        return parents_list

    def getAllParents(self, child_id):
        items = []
        items.extend(self.items)
        self.start = 0
        self.end = len(items) - 1
        self.mid = 0
        all_parents_list = []
        parent_id = self.getItem(child_id).get('parent')
        try:
            while self.end >= self.start:
                self.mid = (self.end + self.start) // 2
                if items[self.mid].get('id') == parent_id:
                    if items[self.mid].get('parent') == 'root':
                        all_parents_list.append(items[self.mid])
                        items.pop(self.mid)
                    else:
                        parent_id = items[self.mid].get('parent')
                        all_parents_list.append(items[self.mid])
                        items.pop(self.mid)
                elif items[self.mid].get('id') > parent_id:
                    self.end -= 1
                elif items[self.mid].get('id') < parent_id:
                    self.end += 1
        except IndexError:
            pass
        return all_parents_list


items = [
    {"id": 1, "parent": "root"},
    {"id": 2, "parent": 1, "type": "test"},
    {"id": 3, "parent": 1, "type": "test"},
    {"id": 4, "parent": 2, "type": "test"},
    {"id": 5, "parent": 2, "type": "test"},
    {"id": 6, "parent": 2, "type": "test"},
    {"id": 7, "parent": 4, "type": None},
    {"id": 8, "parent": 4, "type": None}
]
ts = TreeStore(items)
ts.getAll()
ts.getItem(7)
ts.getChildren(4)
ts.getChildren(5)
ts.getAllParents(7)

# Примеры использования:
#  - ts.getAll() // [{"id":1,"parent":"root"},{"id":2,"parent":1,"type":"test"},{"id":3,"parent":1,"type":"test"},{"id":4,"parent":2,"type":"test"},{"id":5,"parent":2,"type":"test"},{"id":6,"parent":2,"type":"test"},{"id":7,"parent":4,"type":None},{"id":8,"parent":4,"type":None}]
#
#  - ts.getItem(7) // {"id":7,"parent":4,"type":None}
#
#  - ts.getChildren(4) // [{"id":7,"parent":4,"type":None},{"id":8,"parent":4,"type":None}]
#  - ts.getChildren(5) // []
#
#  - ts.getAllParents(7) // [{"id":4,"parent":2,"type":"test"},{"id":2,"parent":1,"type":"test"},{"id":1,"parent":"root"}]
