# vero
import { useState } from 'react';
import { ShoppingCart } from 'lucide-react';
import { Card, CardContent } from '@/components/ui/card';
import { Button } from '@/components/ui/button';

const products = [
  { id: 1, name: "Velvet Dress", price: 120, image: "/images/velvet-dress.jpg" },
  { id: 2, name: "Leather Jacket", price: 220, image: "/images/leather-jacket.jpg" },
  { id: 3, name: "Silk Blouse", price: 90, image: "/images/silk-blouse.jpg" },
];

export default function Home() {
  const [cart, setCart] = useState([]);

  const addToCart = (product) => {
    setCart([...cart, product]);
  };

  return (
    <div className="min-h-screen bg-gray-950 text-white p-6">
      <header className="flex justify-between items-center mb-10">
        <h1 className="text-3xl font-bold">Veroshi</h1>
        <div className="flex items-center gap-2">
          <ShoppingCart />
          <span>{cart.length}</span>
        </div>
      </header>

      <section className="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 gap-6">
        {products.map((product) => (
          <Card key={product.id} className="bg-gray-900 rounded-2xl p-4">
            <CardContent className="flex flex-col items-center">
              <img src={product.image} alt={product.name} className="w-48 h-64 object-cover rounded-xl mb-4" />
              <h2 className="text-xl font-semibold mb-2">{product.name}</h2>
              <p className="text-lg mb-4">${product.price}</p>
              <Button onClick={() => addToCart(product)} className="bg-pink-600 hover:bg-pink-700">
                Add to Cart
              </Button>
            </CardContent>
          </Card>
        ))}
      </section>
    </div>
  );
}
